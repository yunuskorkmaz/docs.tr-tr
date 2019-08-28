---
title: BackgroundWorker Bileşenine Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- BackgroundWorker
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 64e9b3ab-7443-4a77-ab17-b8b8c0cb3f62
ms.openlocfilehash: e91d74b7ca5515dd63ba17a9111cadf5090dae2a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046100"
---
# <a name="backgroundworker-component-overview"></a>BackgroundWorker Bileşenine Genel Bakış
Yürütülmesi uzun zaman alabilir çok sayıda gerçekleştirilen işlem vardır. Örneğin:  
  
- Görüntü İndirmeleri  
  
- Web hizmeti etkinleştirmeleri  
  
- Dosya indirmeleri ve karşıya yüklemeleri (eşler arası uygulamalar için de dahil)  
  
- Karmaşık yerel hesaplamalar  
  
- Veritabanı işlemleri  
  
- Yerel disk erişimi, bellek erişimine göre yavaş hız olarak verildi  
  
 Bunlar gibi işlemler, Kullanıcı arabiriminize çalışırken engel olmasına neden olabilir. Yanıt veren bir kullanıcı arabirimi istediğinizde ve söz konusu işlemlerle ilişkili uzun gecikmeler varsa, <xref:System.ComponentModel.BackgroundWorker> bileşen kullanışlı bir çözüm sağlar.  
  
 <xref:System.ComponentModel.BackgroundWorker> Bileşen, uygulamanızın ana kullanıcı arabirimi iş parçacığından farklı bir iş parçacığında zaman uyumsuz işlemleri ("arka planda") yürütme yeteneği sağlar. Bir <xref:System.ComponentModel.BackgroundWorker>kullanmak için, arka planda hangi zaman tüketen çalışan yönteminin yürütüleceğini ve sonra <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> yöntemi çağırılacağını söylemeniz yeterlidir. Çalışan yöntemi zaman uyumsuz olarak çalışırken, çağıran iş parçacığınız normal şekilde çalışmaya devam eder. Yöntem tamamlandığında <xref:System.ComponentModel.BackgroundWorker> , isteğe bağlı olarak işlemin sonuçlarını içeren <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> olayı tetikleyerek çağıran iş parçacığını uyarır.  
  
 Bileşen araç kutusundan, **Bileşenler** sekmesinde kullanılabilir. <xref:System.ComponentModel.BackgroundWorker> Formunuza bir <xref:System.ComponentModel.BackgroundWorker> eklemek için, <xref:System.ComponentModel.BackgroundWorker> bileşeni formunuza sürükleyin. Bileşen tepsisinde görünür ve özellikleri **Özellikler** penceresinde görünür.  
  
 Zaman uyumsuz işleminizi başlatmak için <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> yöntemini kullanın. <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>, çalışan yönteminizin `object` bağımsız değişkenlerini geçirmek için kullanılabilen isteğe bağlı bir parametre alır. Sınıfı, çalışan iş <xref:System.ComponentModel.BackgroundWorker.DoWork> parçacığınız bir <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi aracılığıyla bağlı olan olayı ortaya koyar. <xref:System.ComponentModel.BackgroundWorker>  
  
 Olay işleyicisi bir <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> özelliği olan <xref:System.ComponentModel.DoWorkEventArgs> bir parametre alır. <xref:System.ComponentModel.BackgroundWorker.DoWork> Bu özellik öğesinden <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> parametresini alır ve <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisinde çağrılabilecek çalışan yöntemine geçirilebilir. Aşağıdaki örnekte, adlı `ComputeFibonacci`bir çalışan yönteminden bir sonucun nasıl atanacağı gösterilmektedir. Daha büyük bir örnek bir parçasıdır ve bu, [nasıl yapılır: Arka plan Işlemi](how-to-implement-a-form-that-uses-a-background-operation.md)kullanan bir form uygulayın.  
  
 [!code-cpp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
 [!code-vb[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
 Olay işleyicilerini kullanma hakkında daha fazla bilgi için bkz. [Olaylar](../../../standard/events/index.md).  
  
> [!CAUTION]
> Herhangi bir sıralamanın çoklu iş parçacığı kullanımı kullanılırken, kendinizi çok önemli ve karmaşık hatalara maruz kalırsınız. Çoklu iş parçacığı kullanan herhangi bir çözümü uygulamadan önce, [yönetilen Iş parçacığı En Iyi uygulamalarına](../../../standard/threading/managed-threading-best-practices.md) danışın.  
  
 <xref:System.ComponentModel.BackgroundWorker> Sınıfını kullanma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Bir Işlemi arka planda](how-to-run-an-operation-in-the-background.md)çalıştırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen Iş parçacığı](../../../standard/threading/index.md)
- [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Nasıl yapılır: Arka plan Işlemi kullanan bir form uygulama](how-to-implement-a-form-that-uses-a-background-operation.md)
