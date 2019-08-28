---
title: 'Nasıl yapılır: Arka Plan İşlemi Kullanan Bir Form Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [Windows Forms], forms
- BackgroundWorker component
- background tasks
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- background threads
- threading [Windows Forms], background operations
- background operations
ms.assetid: 9f483f93-1613-4be1-a021-b4934e9c78f3
ms.openlocfilehash: e06b18558f6b3fa3cef47613bbaef16fb7c740f0
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046200"
---
# <a name="how-to-implement-a-form-that-uses-a-background-operation"></a>Nasıl yapılır: Arka Plan İşlemi Kullanan Bir Form Uygulama
Aşağıdaki örnek program Fibonaccı numaralarını hesaplayan bir form oluşturur. Hesaplama, Kullanıcı arabirimi iş parçacığından ayrı bir iş parçacığında çalışır, bu nedenle hesaplama ilerledikçe Kullanıcı arabirimi gecikmeler olmadan çalışmaya devam eder.  
  
 Visual Studio 'da bu görev için kapsamlı destek vardır.  
  
 Ayrıca bkz [. İzlenecek yol: Arka plan Işlemi](walkthrough-implementing-a-form-that-uses-a-background-operation.md)kullanan bir form uygulama.  
  
## <a name="example"></a>Örnek  
 [!code-cpp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#1)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System, System. Drawing ve System. Windows. Forms derlemelerine başvurular.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
  
> [!CAUTION]
> Herhangi bir sıralamanın çoklu iş parçacığı kullanımı kullanılırken, kendinizi çok önemli ve karmaşık hatalara maruz kalırsınız. Çoklu iş parçacığı kullanan herhangi bir çözümü uygulamadan önce, [yönetilen Iş parçacığı En Iyi uygulamalarına](../../../standard/threading/managed-threading-best-practices.md) danışın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri](../../../standard/threading/managed-threading-best-practices.md)
