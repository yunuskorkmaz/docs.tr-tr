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
ms.openlocfilehash: df7c6caf7b23824a596e94e1bd62205907b0b56a
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592414"
---
# <a name="how-to-implement-a-form-that-uses-a-background-operation"></a>Nasıl yapılır: Arka Plan İşlemi Kullanan Bir Form Uygulama
Aşağıdaki örnek program Fibonacci numaraları hesaplayan bir form oluşturur. Hesaplama kullanıcı arabirimi hesaplama devam ettikçe gecikmeler çalışmaya devam eder, kullanıcı arabirimi iş parçacığından ayrı bir iş parçacığında çalışır.  
  
 Visual Studio'da bu görevi için kapsamlı desteği yoktur.  
  
 Ayrıca bkz: [izlenecek yol: Arka plan işlemi kullanan bir Form uygulama](walkthrough-implementing-a-form-that-uses-a-background-operation.md).  
  
## <a name="example"></a>Örnek  
 [!code-cpp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#1)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
- Sistem, System.Drawing ve System.Windows.Forms derlemelere başvuruları.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
  
> [!CAUTION]
>  Her türlü çoklu iş parçacığı kullanırken, büyük olasılıkla kendiniz çok önemli ve karmaşık hataları ortaya çıkarır. Başvurun [yönetilen iş parçacığı oluşturma en iyi yöntemler](../../../standard/threading/managed-threading-best-practices.md) kullanan herhangi bir çözümü uygulamadan önce çoklu iş parçacığı kullanımı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri](../../../standard/threading/managed-threading-best-practices.md)
