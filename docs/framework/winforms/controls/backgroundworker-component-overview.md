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
ms.openlocfilehash: da1d87464ef30fb549a2c201170e81c45cbdf6fc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64587734"
---
# <a name="backgroundworker-component-overview"></a>BackgroundWorker Bileşenine Genel Bakış
Yürütmek için uzun bir zaman alabilir çok sık gerçekleştirilen işlemler vardır. Örneğin:  
  
- Görüntüyü indirir  
  
- Web hizmeti çağrıları  
  
- Dosya indirir ve yükler (eşler arası uygulamalar dahil)  
  
- Karmaşık yerel hesaplamalar  
  
- Veritabanı işlemleri  
  
- Göreli bellek erişimi yavaş hızını verilen, yerel disk erişimi  
  
 Bunlar gibi işlemler, bunlar çalışırken kesmek, kullanıcı arabirimi neden olabilir. Duyarlı bir kullanıcı Arabirimi istediğiniz ve uzun gecikmeler gibi işlemlerle ilişkili ile karşı karşıya kalmaktadır <xref:System.ComponentModel.BackgroundWorker> bileşeni, uygun bir çözüm sağlar.  
  
 <xref:System.ComponentModel.BackgroundWorker> Bileşen zaman uyumsuz olarak ("arka planda"), zaman alıcı işlemleri yürütmek için yeteneği sağlar, uygulamanızın ana UI iş parçacığından farklı bir iş parçacığı üzerinde. Kullanılacak bir <xref:System.ComponentModel.BackgroundWorker>, yalnızca arka planda yürütülmesi için ne zaman çalışan yöntemi bildirmek ve ardından çağırmanızı <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> yöntemi. Çağıran iş parçacığını çalışan yöntemin zaman uyumsuz olarak çalışırken normal şekilde çalışmaya devam eder. Yöntemi tamamlandığında <xref:System.ComponentModel.BackgroundWorker> Açmadığınızda tarafından çağıran iş parçacığını uyarıları <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> isteğe bağlı olarak işlemin sonuçlarını içeren olay.  
  
 <xref:System.ComponentModel.BackgroundWorker> Bileşen kullanılabilir **araç kutusu**, **bileşenleri** sekmesi. Eklemek için bir <xref:System.ComponentModel.BackgroundWorker> formunuza sürükleyin <xref:System.ComponentModel.BackgroundWorker> formunuza bileşen. Bileşen tepsisinde görünür ve özelliklerini görünür **özellikleri** penceresi.  
  
 Zaman uyumsuz işlemi başlatmak için <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> yöntemi. <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> İsteğe bağlı alan `object` çalışan yönteminize bağımsız değişkenleri geçirmek için kullanılan parametre. <xref:System.ComponentModel.BackgroundWorker> Sınıfı kullanıma sunan <xref:System.ComponentModel.BackgroundWorker.DoWork> olayı, kendisine, iş parçacığı bağlı aracılığıyla bir <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi.  
  
 <xref:System.ComponentModel.BackgroundWorker.DoWork> Olay işleyicisini alır bir <xref:System.ComponentModel.DoWorkEventArgs> olan parametre bir <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> özelliği. Bu özellik parametresinden alır <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> ve çağırılacak olan çalışan yönteminize iletilen <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi. Aşağıdaki örnek adlı bir çalışan yöntemden bir sonuç atama gösterir `ComputeFibonacci`. Konumunda bulabilirsiniz daha büyük bir örneğin parçasıdır [nasıl yapılır: Arka plan işlemi kullanan bir Form uygulama](how-to-implement-a-form-that-uses-a-background-operation.md).  
  
 [!code-cpp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
 [!code-vb[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
 Olay işleyicileri kullanma hakkında daha fazla bilgi için bkz. [olayları](../../../standard/events/index.md).  
  
> [!CAUTION]
>  Her türlü çoklu iş parçacığı kullanırken, büyük olasılıkla kendiniz çok önemli ve karmaşık hataları ortaya çıkarır. Başvurun [yönetilen iş parçacığı oluşturma en iyi yöntemler](../../../standard/threading/managed-threading-best-practices.md) kullanan herhangi bir çözümü uygulamadan önce çoklu iş parçacığı kullanımı.  
  
 Kullanma hakkında daha fazla bilgi için <xref:System.ComponentModel.BackgroundWorker> sınıfı [nasıl yapılır: Arka planda işlem çalıştırma](how-to-run-an-operation-in-the-background.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen iş parçacığı oluşturma](../../../standard/threading/index.md)
- [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Nasıl yapılır: Arka plan işlemi kullanan bir Form uygulama](how-to-implement-a-form-that-uses-a-background-operation.md)
