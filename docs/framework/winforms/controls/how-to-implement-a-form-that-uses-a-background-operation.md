---
title: 'Nasıl yapılır: Arka Plan İşlemi Kullanan Bir Form Uygulama'
description: Başka bir işlem devam ederken bir işlemin çalışmaya devam edebilmesi için bir arka plan işlemi kullanan bir Windows formu uygulamayı öğrenin.
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
ms.openlocfilehash: 23bf4bc02fbf998d92dfce6d84e4e337cbefe7d9
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174529"
---
# <a name="how-to-implement-a-form-that-uses-a-background-operation"></a>Nasıl yapılır: Arka Plan İşlemi Kullanan Bir Form Uygulama
Aşağıdaki örnek program Fibonaccı numaralarını hesaplayan bir form oluşturur. Hesaplama, Kullanıcı arabirimi iş parçacığından ayrı bir iş parçacığında çalışır, bu nedenle hesaplama ilerledikçe Kullanıcı arabirimi gecikmeler olmadan çalışmaya devam eder.  
  
 Visual Studio 'da bu görev için kapsamlı destek vardır.  
  
 Ayrıca bkz. [Izlenecek yol: arka plan Işlemi kullanan bir form uygulama](walkthrough-implementing-a-form-that-uses-a-background-operation.md).  
  
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
