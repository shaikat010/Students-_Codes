import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        //scanner
        Scanner scanner = new Scanner(System.in);

        //ticket prices
        final float[] ticket_one_day_prices = {20, 12, 16, 60, 15};
        final float[] ticket_two_day_prices = {30, 18, 24, 90, 22.5f};

        //inputs
        int day_of_week = 0;
        int days_in_a_row = 0;
        int type_of_ticket = 0;
        int amount_of_tickets = 0;
        int type_of_attraction = 0;
        int replace_tickets = 0;

        //extra attraction prices
        final float[] attraction_prices = {2.5f, 2, 5};

        //misc
        final String[] week = {"Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"};
        int children_available = 0;

        //loops
        int continue_ticket_purchase = 1;
        int continue_attraction_purchase = 1;
        int continue_booking = 1;

        //outputs
        int[] number_of_tickets_buying = {0, 0, 0, 0, 0};
        boolean[] extra_attractions_bought = {false, false, false};
        int total_tickets = 0;
        float attractions_cost = 0;
        float final_cost = 0f;
        int booking_number = 0;

        //alternate prices
        boolean alternate_prices_possible = false;
        float alternate_group_price = 0;
        float alternate_family_price = 0;
        boolean family_is_better = false;
        int[] alternate_number_of_tickets_buying = {0, 0, 0, 0, 0};



        while (continue_booking == 1) {

            day_of_week = 0;
            days_in_a_row = 0;
            type_of_ticket = 0;
            amount_of_tickets = 0;
            type_of_attraction = 0;
            replace_tickets = 0;
            children_available = 0;
            continue_ticket_purchase = 1;
            continue_attraction_purchase = 1;
            total_tickets = 0;
            attractions_cost = 0;
            final_cost = 0f;
            alternate_prices_possible = false;
            alternate_group_price = 0;
            alternate_family_price = 0;
            family_is_better = false;
            for (int i = 0; i < 5; i++) {
                number_of_tickets_buying[i] = 0;
            }
            for (int i = 0; i < 3; i++) {
                extra_attractions_bought[i] = false;
            }
            for (int i = 0; i < 5; i++) {
                alternate_number_of_tickets_buying[i] = 0;
            }



            //day to book (task 1)
            System.out.println("Bookings available upto a week in advance.");
            System.out.println("Days available: ");
            for (int i = 0; i < 7; i++) {
                System.out.println(" - " + i + ") " + week[i]);
            }


            //day of week to book on (task 2)
            System.out.println("");
            System.out.print("Which day would you like to book your ticket? (type the number above to pick):");
            day_of_week = scanner.nextInt();
            while (day_of_week < 0 || day_of_week > 6) { //validation
                System.out.print("Wrong input. please type a number from 0 to 6: ");
                day_of_week = scanner.nextInt();
            }

            //days to book for
            System.out.println("");
            System.out.print("Would you like to book 1 or 2 days in a row? (type 1 for 1 day, or 2 for 2 days): ");
            days_in_a_row = scanner.nextInt();
            while (days_in_a_row < 1 || days_in_a_row > 2) { //validation
                System.out.print("Wrong input. please type either 1 or 2: ");
                days_in_a_row = scanner.nextInt();
            }
            days_in_a_row = days_in_a_row - 1;





            //ticket purchase
            while (continue_ticket_purchase == 1) {

                //tickets (task 1)
                System.out.println();
                System.out.println("Prices:                                                     1 day    2 days");
                System.out.println("Normal Tickets");
                System.out.println("  - 0) Adults                                             : " + ticket_one_day_prices[0] + "0$ / " + ticket_two_day_prices[0] + "0$");
                System.out.println("  - 1) Children (Two per adult)                           : " + ticket_one_day_prices[1] + "0$ / " + ticket_two_day_prices[1] + "0$");
                System.out.println("  - 2) Seniors                                            : " + ticket_one_day_prices[2] + "0$ / " + ticket_two_day_prices[2] + "0$");
                System.out.println("Special Tickets:");
                System.out.println("  - 3) Family (Upto two adults or seniors, and 3 children): " + ticket_one_day_prices[3] + "0$ / " + ticket_two_day_prices[3] + "0$");
                System.out.println("  - 4) Group  (Six or more. Price per person)             : " + ticket_one_day_prices[4] + "0$ / " + ticket_two_day_prices[4] + "0$");


                //ticket type to buy (task 2)
                System.out.println("");
                System.out.print("Which ticket Would you like to buy? (pick a number above) (Children tickets available: " + children_available + "):");
                type_of_ticket = scanner.nextInt();
                while ((type_of_ticket < 0 || type_of_ticket > 4) || (type_of_ticket == 1 && children_available <= 0)) { //validation
                    if (type_of_ticket == 1 && children_available <= 0) {
                        System.out.print("You have no children tickets available. Please pick another ticket:");
                    } else {
                        System.out.print("Wrong input. please type a number from 0 to 4: ");
                    }
                    type_of_ticket = scanner.nextInt();
                }


                //amount of tickets to buy
                System.out.println("");
                System.out.print("How many of this ticket would you like to buy? (minimum 6 for Groups) :");
                amount_of_tickets = scanner.nextInt();
                while (amount_of_tickets < 1 || (type_of_ticket == 4 && amount_of_tickets < 6) || (type_of_ticket == 1 && amount_of_tickets > children_available)) { //validation
                    if (type_of_ticket == 4 && amount_of_tickets < 6) {
                        System.out.print("Minimum of 6 tickets must be bought for groups: ");
                    } else if (type_of_ticket == 1 && amount_of_tickets > children_available) {
                        System.out.print("Maximum of " + children_available + " tickets can be bought for children at the moment: ");
                    } else {
                        System.out.print("Wrong input. please type a number above 0: ");
                    }
                    amount_of_tickets = scanner.nextInt();
                }

                //add to array
                number_of_tickets_buying[type_of_ticket] += amount_of_tickets;


                //children calculations
                if (type_of_ticket == 0 || type_of_ticket == 2) {children_available += (2 * amount_of_tickets);}
                if (type_of_ticket == 1) {children_available -= amount_of_tickets;}


                //continue?
                System.out.print("Would you like to buy more tickets? (0: no | 1: yes) :");
                continue_ticket_purchase = scanner.nextInt();
                while (continue_ticket_purchase < 0 || continue_ticket_purchase > 1) { //validation
                    System.out.print("Wrong input. please type either 1 or 0: ");
                    continue_ticket_purchase = scanner.nextInt();
                }
            }





            //attraction purchase
            while (continue_attraction_purchase == 1) {
                //attractions (task 1)
                System.out.println("");
                System.out.println("Would you like to add any additional attractions?");
                System.out.println("Additional Attractions (per person):");
                System.out.println("  - 0) lion feeding                                       : " + attraction_prices[0] + "0$");
                System.out.println("  - 1) penguin feeding                                    : " + attraction_prices[1] + "0$");
                if (days_in_a_row == 1) {
                    System.out.println("  - 2) evening barbecue (two days only)                   : " + attraction_prices[2] + "0$");
                }

                //attraction to buy (task 2)
                System.out.print("Which one would you like to purchase?: ");
                type_of_attraction = scanner.nextInt();
                while ((type_of_attraction < 0) || (type_of_attraction > 2 && days_in_a_row == 1) || (type_of_attraction > 1 && days_in_a_row == 0) || (extra_attractions_bought[type_of_attraction])) { //validation
                    if ((type_of_attraction < 0 || type_of_attraction > 2) && days_in_a_row == 1) {
                        System.out.print("Wrong input. please type a number from 0 to 2: ");
                    } else if ((type_of_attraction < 0 || type_of_attraction > 1) && days_in_a_row == 0) {
                        System.out.print("Wrong input. please type a number from 0 to 1: ");
                    }  else if (extra_attractions_bought[type_of_attraction]) {
                        System.out.print("Attraction already chosen. please pick another attraction: ");
                    }
                    type_of_attraction = scanner.nextInt();
                }

                extra_attractions_bought[type_of_attraction] = true;

                //leave if all attractions have been bought
                if ((extra_attractions_bought[0] && extra_attractions_bought[1] && extra_attractions_bought[2] && days_in_a_row == 1)) {
                    break;
                }
                if (extra_attractions_bought[0] && extra_attractions_bought[1] && days_in_a_row == 0) {
                    break;
                }

                //continue?
                System.out.print("Would you like to buy more attractions? (0: no | 1: yes): ");
                continue_attraction_purchase = scanner.nextInt();
                while (continue_attraction_purchase < 0 || continue_attraction_purchase > 1) { //validation
                    System.out.print("Wrong input. please type either 1 or 0: ");
                    continue_attraction_purchase = scanner.nextInt();
                }
            }





            //final cost calculations
            total_tickets = number_of_tickets_buying[0] + number_of_tickets_buying[1] + number_of_tickets_buying[2] + (number_of_tickets_buying[3] * 5) + number_of_tickets_buying[4];

            for (int i = 0; i < 3; i++) {
                if (extra_attractions_bought[i]) {attractions_cost += total_tickets * attraction_prices[i];}
            }

            days_in_a_row += 1;

            if (days_in_a_row == 1) {
                for (int i = 0; i < 5; i++) {final_cost += (number_of_tickets_buying[i] * ticket_one_day_prices[i]);}
            } else if (days_in_a_row == 2) {
                for (int i = 0; i < 5; i++) {final_cost += (number_of_tickets_buying[i] * ticket_two_day_prices[i]);}
            }


            //alternate calculations
            if (total_tickets >= 6 || ((number_of_tickets_buying[0] >= 2 || number_of_tickets_buying[2] >= 2) && number_of_tickets_buying[1] >= 3)) {
                alternate_prices_possible = true;
                alternate_number_of_tickets_buying = number_of_tickets_buying;

                if (total_tickets >= 6) {
                    if (days_in_a_row == 1) {
                        alternate_group_price = total_tickets * ticket_one_day_prices[4];
                    } else if (days_in_a_row == 2) {
                        alternate_group_price = total_tickets * ticket_two_day_prices[4];
                    }
                    alternate_group_price += attractions_cost;
                }

                while ((alternate_number_of_tickets_buying[0] >= 2 || alternate_number_of_tickets_buying[2] >= 2) && alternate_number_of_tickets_buying[1] >= 3) {
                    alternate_number_of_tickets_buying[1] -= 3;

                    if (alternate_number_of_tickets_buying[0] > 2) {
                        alternate_number_of_tickets_buying[0] -= 2;
                    } else if (alternate_number_of_tickets_buying[2] > 2) {
                        alternate_number_of_tickets_buying[2] -= 2;
                    }
                    alternate_number_of_tickets_buying[3] += 1;
                }
                if (days_in_a_row == 1) {
                    for (int i = 0; i < 5; i++) {alternate_family_price += (alternate_number_of_tickets_buying[i] * ticket_one_day_prices[i]);}
                } else if (days_in_a_row == 2) {
                    for (int i = 0; i < 5; i++) {alternate_family_price += (alternate_number_of_tickets_buying[i] * ticket_two_day_prices[i]);}
                }
                alternate_family_price += attractions_cost;

                if (alternate_family_price < alternate_group_price) {
                    family_is_better = true;
                }

            }


            final_cost += attractions_cost;

            System.out.println("");
            System.out.println("");
            System.out.println("");
            System.out.println("You are booking:");
            System.out.println("Adult tickets    : " + number_of_tickets_buying[0]);
            System.out.println("Children tickets : " + number_of_tickets_buying[1]);
            System.out.println("Senior tickets   : " + number_of_tickets_buying[2]);
            System.out.println("Family tickets   : " + number_of_tickets_buying[3]);
            System.out.println("Group tickets    : " + number_of_tickets_buying[4]);
            System.out.println("");
            System.out.println("Along with these attractions:");
            System.out.println("Lion feeding     :" + extra_attractions_bought[0]);
            System.out.println("Penguin feeding  :" + extra_attractions_bought[1]);
            System.out.println("Evening barbecue :" + extra_attractions_bought[2]);
            System.out.println("");
            System.out.println("For " + days_in_a_row + " day(s) in a row on " + week[day_of_week]);
            System.out.println("For a total price of: " + final_cost + "0$");
            System.out.println("");
            if (alternate_prices_possible) {
                System.out.print("However if tickets are ");
                if (family_is_better) {
                    System.out.println("bought in the following way, costs can be reduced: ");
                    System.out.println("Adult tickets    : " + alternate_number_of_tickets_buying[0]);
                    System.out.println("Children tickets : " + alternate_number_of_tickets_buying[1]);
                    System.out.println("Senior tickets   : " + alternate_number_of_tickets_buying[2]);
                    System.out.println("Family tickets   : " + alternate_number_of_tickets_buying[3]);
                    System.out.println("Group tickets    : " + alternate_number_of_tickets_buying[4]);
                } else {
                    System.out.println("replaced with group tickets, then costs can be reduced.");
                }
                System.out.println("");
                System.out.print("Would you like to replace prices? (0: no | 1: yes): ");
                replace_tickets = scanner.nextInt();
                while (replace_tickets < 0 || replace_tickets > 1) { //validation
                    System.out.print("Wrong input. please type either 1 or 0: ");
                    replace_tickets = scanner.nextInt();
                }
                if (replace_tickets == 1) {
                    if (family_is_better) {
                        number_of_tickets_buying = alternate_number_of_tickets_buying;
                        final_cost = alternate_family_price;
                    } else {
                        number_of_tickets_buying[0] = 0;
                        number_of_tickets_buying[1] = 0;
                        number_of_tickets_buying[2] = 0;
                        number_of_tickets_buying[3] = 0;
                        number_of_tickets_buying[4] = total_tickets;
                        final_cost = alternate_group_price;
                    }
                    System.out.println("Your final price is: " + final_cost + "0$");
                }

            }



            System.out.println("Your booking number is:" + booking_number);
            System.out.println("");


            System.out.println("Thank you for purchasing!");

            booking_number += 1;

            //continue?
            System.out.println("");
            System.out.print("Would you like book again? (0: no | 1: yes): ");
            continue_booking = scanner.nextInt();
            while (continue_booking < 0 || continue_booking > 1) { //validation
                System.out.print("Wrong input. please type either 1 or 0: ");
                continue_booking = scanner.nextInt();
            }

        }

    }

}
