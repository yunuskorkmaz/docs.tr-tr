---
title: "BackgroundWorker Bileşenine Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
f1_keywords: BackgroundWorker
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f192081d9b7e30f10373342aef39443ff49e9931
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="backgroundworker-component-overview"></a>BackgroundWorker Bileşenine Genel Bakış
Yürütmek için uzun zaman alabilir pek çok sık gerçekleştirilen işlemler vardır. Örneğin:  
  
-   Görüntüyü indirir  
  
-   Web hizmeti çağrıları  
  
-   Dosyası indirilir ve (eşler arası uygulamaları dahil) yükler  
  
-   Karmaşık yerel hesaplamalar  
  
-   Veritabanı işlemleri  
  
-   Göreli bellek erişimi yavaş hızı verilen yerel disk erişimi  
  
 Bunlar gibi işlemleri Kullanıcı Arabiriminizin çalıştıkları sırada askıda kalmasına neden olabilir. Bir yanıt veren UI istediğiniz ve gecikmelere gibi işlemlerle ilişkili ile karşılaştığı <xref:System.ComponentModel.BackgroundWorker> bileşeni, uygun bir çözüm sağlar.  
  
 <xref:System.ComponentModel.BackgroundWorker> Bileşen imkanı sunar, zaman uyumsuz olarak ("arka planda"), zaman alıcı işlemlerini yürütmek için uygulamanızın ana kullanıcı Arabirimi iş parçacığından farklı bir iş parçacığı üzerinde. Kullanılacak bir <xref:System.ComponentModel.BackgroundWorker>, yalnızca arka planda yürütmek için ne zaman çalışan yöntem bildirin ve size çağrısı <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> yöntemi. Çağıran, iş parçacığı çalışan yöntemi zaman uyumsuz olarak çalışırken normal şekilde çalışmaya devam eder. Yöntem tamamlandığında <xref:System.ComponentModel.BackgroundWorker> çağıran iş parçacığı tarafından tetikleme uyarıları <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> isteğe bağlı olarak işlemi sonuçlarını içeren olay.  
  
 <xref:System.ComponentModel.BackgroundWorker> Bileşen edinilebilir **araç**, **bileşenleri** sekmesi. Eklemek için bir <xref:System.ComponentModel.BackgroundWorker> formunuza sürükleyin <xref:System.ComponentModel.BackgroundWorker> formunuza bileşen. Bileşen tepsisinde görünür ve özelliklerini görüntülenmesini **özellikleri** penceresi.  
  
 Zaman uyumsuz işlemi başlatmak için kullanmak <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> yöntemi. <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>İsteğe bağlı bir alan `object` çalışan yönteminizi bağımsız değişkenleri geçirmek için kullanılan parametre. <xref:System.ComponentModel.BackgroundWorker> Sınıf çıkarır <xref:System.ComponentModel.BackgroundWorker.DoWork> için çalışan iş parçacığı kullanıma açılmış üzerinden olay, bir <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi.  
  
 <xref:System.ComponentModel.BackgroundWorker.DoWork> Olay işleyicisi geçen bir <xref:System.ComponentModel.DoWorkEventArgs> sahip parametresi bir <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> özelliği. Bu özellik parametreyi alır <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> ve çağrılacağı içinde çalışan yönteminize iletilen <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi. Aşağıdaki örnek, bir sonucu olarak adlandırılan bir alt yöntemden atamak gösterilmiştir `ComputeFibonacci`. Konumunda bulabilirsiniz daha büyük bir örneğin parçasıdır [nasıl yapılır: bir arka plan işlemi kullanan bir Form uygulama](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).  
  
 [!code-cpp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
 [!code-vb[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
 Olay işleyicileri kullanma hakkında daha fazla bilgi için bkz: [olayları](../../../../docs/standard/events/index.md).  
  
> [!CAUTION]
>  Her tür çoklu iş parçacığı kullanımı kullanırken, potansiyel olarak kendiniz için çok önemli ve karmaşık hatalar kullanıma sunar. Başvurun [yönetilen iş parçacığı oluşturma en iyi yöntemler](../../../../docs/standard/threading/managed-threading-best-practices.md) kullanan herhangi bir çözümü uygulamadan önce çoklu iş parçacığı kullanımı.  
  
 Kullanma hakkında daha fazla bilgi için <xref:System.ComponentModel.BackgroundWorker> sınıfı için bkz: [nasıl yapılır: bir işlemi arka planda çalışan](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IN derleme değil: Visual Basic'te çoklu iş parçacığı kullanımı](http://msdn.microsoft.com/en-us/c731a50c-09c1-4468-9646-54c86b75d269)  
 [Nasıl yapılır: bir arka plan işlemi kullanan bir Form uygulama](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
