---
layout: single
date: 2020-04-25 12:00:00 +0900
title: supervisor

---

## 문제

총  n개의 시험장이 있고, 각각의 시험장마다 응시자들이 있다.  i번 시험장에 있는 응시자의 수는 Ai명이다.

감독관은 총감독관과 부감독관으로 두 종류가 있다. 총감독관은 한 시험장에서 감시할 수 있는 응시자의 수가 B명이고, 부감독관은 한 시험장에서 감시할 수 있는 응시자의 수가 C명이다.

각각의 시험장에 총감독관은 오직 1명만 있어야 하고, 부감독관은 여러 명 있어도 된다.

각 시험장마다 응시자들을 모두 감시해야 한다. 이때, 필요한 감독관 수의 최솟값을 구하는 프로그램을 작성하시오.



## 입력

첫째 줄에 시험장의 개수 A가 주어진다.

둘째 줄에 각 시험장에 있는 응시자의 수 Ai가 주어진다.

셋째 줄에 B와 C가 주어진다.



*****

## 소스

import java.util.Scanner;

public class supervisor {

	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);
		
		int n = scanner.nextInt(); //시험장의 개수 입력
		int[] array = new int[n]; //시험장을 배열로 표현
		long result = 0;
	
		for (int i = 0; i < n; i++) {
			array[i] = scanner.nextInt(); //각 시험장의 학생 수 입력
		}
	
		int general = scanner.nextInt(); //총감독관의 수
		int acting = scanner.nextInt(); //부감독관의 수
	
		for (int i = 0; i < n; i++) {
			result++; //반복문이 돌아갈 때마다 최소 감독관(총감독관)의 수 1씩 증가
			array[i] -= general; //총감독관은 모든 시험장에 들어가기 때문에 각 시험장에 총감독관이 감독할 수 있는 학생의 수를 빼준다.
	
			if (array[i] > 0) { //총감독관이 감독하는 학생을 빼고도 학생이 남았다면
				result += (array[i] / acting); //남은 학생수를 부감독관이 감독하는 학생수로 나눈 몫을 더한다.
				if((array[i] % acting) > 0)
					result++; //나머지가 있다면 부감독관을 한명 늘린다.
			}
	
		}
		System.out.println(result); //총감독관의 수 출력
		scanner.close();
	}

}