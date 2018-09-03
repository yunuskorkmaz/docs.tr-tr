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
ms.openlocfilehash: 1f7da963db34434ee2631e9e2c0367abbd628656
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43488228"
---
# <a name="backgroundworker-component-overview"></a>BackgroundWorker Bileşenine Genel Bakış
Yürütmek için uzun bir zaman alabilir çok sık gerçekleştirilen işlemler vardır. Örneğin:  
  
-   Görüntüyü indirir  
  
-   Web hizmeti çağrıları  
  
-   Dosya indirir ve yükler (eşler arası uygulamalar dahil)  
  
-   Karmaşık yerel hesaplamalar  
  
-   Veritabanı işlemleri  
  
-   Göreli bellek erişimi yavaş hızını verilen, yerel disk erişimi  
  
 Bunlar gibi işlemler, bunlar çalışırken kesmek, kullanıcı arabirimi neden olabilir. Duyarlı bir kullanıcı Arabirimi istediğiniz ve uzun gecikmeler gibi işlemlerle ilişkili ile karşı karşıya kalmaktadır <xref:System.ComponentModel.BackgroundWorker> bileşeni, uygun bir çözüm sağlar.  
  
 <xref:System.ComponentModel.BackgroundWorker> Bileşen zaman uyumsuz olarak ("arka planda"), zaman alıcı işlemleri yürütmek için yeteneği sağlar, uygulamanızın ana UI iş parçacığından farklı bir iş parçacığı üzerinde. Kullanılacak bir <xref:System.ComponentModel.BackgroundWorker>, yalnızca arka planda yürütülmesi için ne zaman çalışan yöntemi bildirmek ve ardından çağırmanızı <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> yöntemi. Çağıran iş parçacığını çalışan yöntemin zaman uyumsuz olarak çalışırken normal şekilde çalışmaya devam eder. Yöntemi tamamlandığında <xref:System.ComponentModel.BackgroundWorker> Açmadığınızda tarafından çağıran iş parçacığını uyarıları <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> isteğe bağlı olarak işlemin sonuçlarını içeren olay.  
  
 <xref:System.ComponentModel.BackgroundWorker> Bileşen kullanılabilir **araç kutusu**, **bileşenleri** sekmesi. Eklemek için bir <xref:System.ComponentModel.BackgroundWorker> formunuza sürükleyin <xref:System.ComponentModel.BackgroundWorker> formunuza bileşen. Bileşen tepsisinde görünür ve özelliklerini görünür **özellikleri** penceresi.  
  
 Zaman uyumsuz işlemi başlatmak için <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> yöntemi. <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> İsteğe bağlı alan `object` çalışan yönteminize bağımsız değişkenleri geçirmek için kullanılan parametre. <xref:System.ComponentModel.BackgroundWorker> Sınıfı kullanıma sunan <xref:System.ComponentModel.BackgroundWorker.DoWork> olayı, kendisine, iş parçacığı bağlı aracılığıyla bir <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi.  
  
 <xref:System.ComponentModel.BackgroundWorker.DoWork> Olay işleyicisini alır bir <xref:System.ComponentModel.DoWorkEventArgs> olan parametre bir <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> özelliği. Bu özellik parametresinden alır <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> ve çağırılacak olan çalışan yönteminize iletilen <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi. Aşağıdaki örnek adlı bir çalışan yöntemden bir sonuç atama gösterir `ComputeFibonacci`. Konumunda bulabilirsiniz daha büyük bir örneğin parçasıdır [nasıl yapılır: arka plan işlemi kullanan bir Form uygulama](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).  
  
 [!code-cpp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
 [!code-vb[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
 Olay işleyicileri kullanma hakkında daha fazla bilgi için bkz. [olayları](../../../../docs/standard/events/index.md).  
  
> [!CAUTION]
>  Her türlü çoklu iş parçacığı kullanırken, büyük olasılıkla kendiniz çok önemli ve karmaşık hataları ortaya çıkarır. Başvurun [yönetilen iş parçacığı oluşturma en iyi yöntemler](../../../../docs/standard/threading/managed-threading-best-practices.md) kullanan herhangi bir çözümü uygulamadan önce çoklu iş parçacığı kullanımı.  
  
 Kullanma hakkında daha fazla bilgi için <xref:System.ComponentModel.BackgroundWorker> sınıfı [nasıl yapılır: arka planda işlem çalıştırma](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IN derleme değil: Visual Basic'te çoklu iş parçacığı kullanımı](https://msdn.microsoft.com/library/c731a50c-09c1-4468-9646-54c86b75d269)  
 [Nasıl yapılır: Arka Plan İşlemi Kullanan Bir Form Uygulama](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
