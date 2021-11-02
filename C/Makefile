# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Makefile                                           :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: amarcell <amarcell@student.42.fr>          +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2021/11/02 15:25:57 by amarcell          #+#    #+#              #
#    Updated: 2021/11/02 15:51:01 by amarcell         ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

# Reset
COLOR_OFF	="\033[0m"       # Text Reset

# Regular Colors
BLACK		=		"\033[0;30m"        # Black
RED			=		"\033[0;31m"          # Red
GREEN		=		"\033[0;32m"        # Green
YELLOW		=		"\033[0;33m"       # Yellow
BLUE		=		"\033[0;34m"         # Blue
PURPLE		=		"\033[0;35m"       # Purple
CYAN		=		"\033[0;36m"         # Cyan
WHITE		=		"\033[0;37m"        # White

# Bold
BBLACK		=		"\033[1;30m       # Black
BRED		=		"\033[1;31m         # Red
BGREEN		=		"\033[1;32m"       # Green
BYELLOW		=		"\033[1;33m"      # Yellow
BBLUE		=		"\033[1;34m"        # Blue
BPURPLE		=		"\033[1;35m"      # Purple
BCYAN		=		"\033[1;36m"        # Cyan
BWHITE		=		"\033[1;37m"       # White

# Underline
UBLACK		=		"\033[4;30m"       # Black
URED		=		"\033[4;31m"         # Red
UGREEN		=		"\033[4;32m"       # Green
UYELLOW		=		"\033[4;33m"      # Yellow
UBLUE		=		"\033[4;34m"        # Blue
UPURPLE		=		"\033[4;35m"      # Purple
UCYAN		=		"\033[4;36m"        # Cyan
UWHITE		=		"\033[4;37m"       # White

#---------------------SRCS---------------------#
#	use the NAME of one color in the COLOR section above --> $(COLOR NAME)

DEBUG_COLOR	=		$(CYAN)
LEAKS_COLOR	=		$(YELLOW)
NORME_TITLE_COLOR =	$(BPURPLE)
NORME_COLOR =		$(PURPLE)

#---------------------SRCS---------------------#

OBJS_DIR	=		objs

OBJS_DEBUG_DIR	=	objs_debug

HS			=		# your h file or nothing, works equally

SRCS		= 		# your c file

EXTRA_CLEAN	=		# extra file do u want delete
				
#---------------------COMPILER---------------------#

# chose a NAME for your program

NAME		=		

C 			= 		@ gcc

CFLAGS		=		-Wall -Wextra -Werror

XFLAGS		=

OBJS		=		$(patsubst %.c, ${OBJS_DIR}/%.o, ${SRCS})

$(OBJS_DIR)/%.o :	./%.c
			@ mkdir -p $(OBJS_DIR)
			$(C) $(CFLAGS) $(XFLAGS) -c $< -o $@

OBJS_DEBUG	=		$(patsubst %.c, ${OBJS_DEBUG_DIR}/%.o, ${SRCS})

$(OBJS_DEBUG_DIR)/%.o :	./%.c
			@ mkdir -p $(OBJS_DEBUG_DIR)
			$(C) $(CFLAGS) $(XFLAGS) -g -c $< -o $@

#---------------------COMMANDS---------------------#

all:		$(NAME)

$(NAME):	$(OBJS)
			@ $(C) $(CFLAGS) $(OBJS) -o $@
			@ echo $(BGREEN) "$(NAME) compiled successfully ✅" $(COLOR_OFF)

clean:
			@ rm -f $(OBJS)
			@ rm -f $(EXTRA_CLEAN)
			@ echo $(BWHITE) "$(NAME) .o files ware successfully deleted 📃➡ 🗑" $(COLOR_OFF)

fclean:		clean
			@ rm -rf $(OBJS_DIR)
			@ rm -rf $(OBJS_DEBUG_DIR)
			@ rm -f $(NAME)
			@ echo $(BWHITE) "$(NAME) file was successfully deleted 🗂 ➡🗑" $(COLOR_OFF)

re:			fclean all
			@ echo $(BGREEN) "$(NAME) recompiled successfully ♻️ ✅" $(COLOR_OFF)

debug:		$(OBJS_DEBUG)
			@ $(C) $(CFLAGS) $(OBJS_DEBUG) -o $(NAME)
			@ echo $(DEBUG_COLOR) "$(NAME) DEBUG compiled successfully  🚫🐛 ✅"
			@ read -p "Press enter to start debugging..."
			@ lldb ./$(NAME)

re-debug:	fclean debug


leaks:		
			@ echo $(LEAKS_COLOR) "[... Finding leaks in $(NAME) ⛳️ ...]" 
			@ leaks --atExit -- ./$(NAME)

clear_space:
			@rm -rf ~/Library/Caches
			@rm -rf ~/Library/Application\ Support/Slack/Cache
			@rm -rf ~/Library/Application\ Support/Slack/Service\ Worker/CacheStorage
			@rm -rf ~/Library/Application\ Support/Code/Crashpad
			@rm -rf ~/Library/Application\ Support/Code/Cache
			@rm -rf ~/Library/Application\ Support/Code/User/workspaceStorage
			@rm -rf ~/Library/Application\ Support/Code/CachedData
			@rm -rf ~/Library/Application\ Support/Chrome/Default
			@rm -rf ~/Library/Developer/CoreSimulator
			@rm -rf ~/Library/Containers/com.docker.docker

norme:		#if no  working norminette on .c files remove the '#' in "@ # norminette $(SRC)"
			@ echo $(NORME_TITLE_COLOR) "-------|norme $(NAME)|-------" $(COLOR_OFF) $(NORME_COLOR)
			@ norminette $(HS)
			@ # norminette $(SRC)
			@ echo $(COLOR_OFF)

.PHONY: 	all clean fclean re norme  debug re-debug leaks clear_space norme