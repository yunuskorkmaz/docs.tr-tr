---
title: "Bir etkinlik örnek AsyncOperationContext kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0888a0bd-d227-4c00-ad6a-b654a01740e8
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ae62192517ee9117092ff11d2da5212d5a1c1fff
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2017
---
# <a name="using-asyncoperationcontext-in-an-activity-sample"></a>Bir etkinlik örnek AsyncOperationContext kullanma
Bu örnek, bir özel geliştirmek gösterilmiştir <xref:System.Activities.CodeActivity> kullanan <xref:System.Activities.AsyncCodeActivityContext> iş akışı dışında zaman uyumsuz olarak gerçekleştirilecek.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Örnek etkinlik kullanan <xref:System.IO.FileStream.BeginWrite%2A> ve <xref:System.IO.FileStream.EndWrite%2A> yöntemlere <xref:System.IO.FileStream> zaman uyumsuz olarak verileri bir dosyaya yazmak için sınıf. Burada sunulan düzeni diğer zaman uyumsuz yöntemleri ile kullanılmak üzere uyarlanabilir. Zaman uyumsuz işlem yürütülürken, diğer etkinlikler iş akışında yürütebilir, ancak iş akışı kalıcı yapılamıyor.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Async.sln örnek çözümü açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Derleme ve çözümü çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\Async`