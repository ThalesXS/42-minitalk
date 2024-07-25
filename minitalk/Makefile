#	====================		Colors			====================

RED = \033[0;31m
GREEN = \033[0;32m
BLUE = \033[0;34m
YELLOW = \033[0;33m
MAGENTA = \033[0;35m
CYAN = \033[0;36m

B_RED = \033[1;31m
B_GREEN = \033[1;32m
B_BLUE = \033[1;34m
L_BLUE = \033[1;94m
B_YELLOW = \033[1;33m
B_MAGENTA = \033[1;35m
B_CYAN = \033[1;36m

RESET = \033[0m

#	====================		Directories		====================

INC = includes
SRC = srcs
SRC_BONUS = srcs_bonus
OBJ_DIR = objects
OBJ_DIR_BONUS = objects_bonus

#	====================		Files			====================

NAME = server client
SERVER = server
T_SERVER = $(B_YELLOW)$(SERVER)$(RESET):
SV_FILES = server.c
SV_OBJ = $(SV_FILES:.c=.o)
CL_FILES = client.c
CL_OBJ = $(CL_FILES:.c=.o)
CLIENT = client
T_CLIENT = $(B_YELLOW)$(CLIENT)$(RESET):
FILES = utils.c
OBJ = $(FILES:.c=.o)
ARQ = minitalk.a
SV_TARGET = $(addprefix $(OBJ_DIR)/, $(OBJ)) $(addprefix $(OBJ_DIR)/, $(SV_OBJ))
CL_TARGET = $(addprefix $(OBJ_DIR)/, $(OBJ)) $(addprefix $(OBJ_DIR)/, $(CL_OBJ))

#	====================		Bonus		====================

BONUS = server_bonus client_bonus
SERVER_BONUS = server_bonus
BT_SERVER = $(B_YELLOW)$(SERVER_BONUS)$(RESET):
SVB_FILES = server_bonus.c
SVB_OBJ = $(SVB_FILES:.c=.o)
CLB_FILES = client_bonus.c
CLB_OBJ = $(CLB_FILES:.c=.o)
CLIENT_BONUS = client_bonus
BT_CLIENT = $(B_YELLOW)$(CLIENT_BONUS)$(RESET):
FILES_BONUS = utils_bonus.c
OBJ_BONUS = $(FILES_BONUS:.c=.o)
ARQ_BONUS = minitalk.a
SVB_TARGET = $(addprefix $(OBJ_DIR_BONUS)/, $(OBJ_BONUS)) $(addprefix $(OBJ_DIR_BONUS)/, $(SVB_OBJ))
CLB_TARGET = $(addprefix $(OBJ_DIR_BONUS)/, $(OBJ_BONUS)) $(addprefix $(OBJ_DIR_BONUS)/, $(CLB_OBJ))

#	====================		Commands	====================

CC = gcc

#	====================		Flags		====================

W = -Wall -Wextra -Werror
O = -c
I = -I $(INC)
WBLOCK = --no-print-directory

LIBFT = -L ./libft -lft

#	====================		Rules		====================

all: $(NAME)

$(NAME): $(OBJ_DIR) $(SV_TARGET) $(CL_TARGET)
	@make -C ./libft $(WBLOCK)
	@$(CC) $(W) $(I) $(SV_TARGET) $(LIBFT) -o $(SERVER)
	@printf "$(T_SERVER) $(GREEN)Library created.\n"
	@$(CC) $(W) $(I) $(CL_TARGET) $(LIBFT) -o $(CLIENT)
	@printf "$(T_CLIENT) $(GREEN)Library created.\n"

$(OBJ_DIR):
	@mkdir -p $(OBJ_DIR)

$(OBJ_DIR)/%.o: $(SRC)/%.c
	$(eval COMPTEUR=$(shell echo $$(($(COMPTEUR)+1))))
	@printf "\e[?25l"
	@if test $(COMPTEUR) -eq 1;then \
		printf "$(B_YELLOW)$(NAME)$(RESET):$(YELLOW) Compiling binary files...$(RESET)\n\n";fi
	@printf "\033[A\33[2K\r\t       $(B_CYAN)Binary $(COMPTEUR):$(CYAN) $@$(RESET)\n"
	@$(CC) $(W) $(O) $(I) $< -o $@

clean:
	@rm -rf $(OBJ_DIR)
	@rm -rf $(OBJ_DIR_BONUS)
	@printf "$(TITLE) $(RED)Binary files deleted.$(RESET)\n"
	@make clean -C ./libft $(WBLOCK)

fclean:
	@rm -f $(SERVER) $(CLIENT)
	@rm -f $(SERVER_BONUS) $(CLIENT_BONUS)
	@rm -rf $(OBJ_DIR)
	@rm -rf $(OBJ_DIR_BONUS)
	@printf "$(TITLE) $(RED)Binary files deleted.$(RESET)\n"
	@printf "$(T_CLIENT) $(RED)Program deleted.$(RESET)\n"
	@printf "$(T_SERVER) $(RED)Program deleted.$(RESET)\n"
	@make fclean -C ./libft $(WBLOCK)

bonus: $(BONUS)

$(BONUS): $(OBJ_DIR_BONUS) $(SVB_TARGET) $(CLB_TARGET)
	@make -C ./libft $(WBLOCK)
	@$(CC) $(W) $(I) $(SVB_TARGET) $(LIBFT) -o $(SERVER_BONUS)
	@printf "$(BT_SERVER) $(GREEN)Library created.\n"
	@$(CC) $(W) $(I) $(CLB_TARGET) $(LIBFT) -o $(CLIENT_BONUS)
	@printf "$(BT_CLIENT) $(GREEN)Library created.\n"

$(OBJ_DIR_BONUS):
	@mkdir -p $(OBJ_DIR_BONUS)

$(OBJ_DIR_BONUS)/%.o: $(SRC_BONUS)/%.c
	$(eval COMPTEUR=$(shell echo $$(($(COMPTEUR)+1))))
	@printf "\e[?25l"
	@if test $(COMPTEUR) -eq 1;then \
		printf "$(B_YELLOW)$(NAME)$(RESET):$(YELLOW) Compiling binary files...$(RESET)\n\n";fi
	@printf "\033[A\33[2K\r\t       $(B_CYAN)Binary $(COMPTEUR):$(CYAN) $@$(RESET)\n"
	@$(CC) $(W) $(O) $(I) $< -o $@

re: fclean all
