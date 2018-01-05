---
title: Yordam etkinlikleri kullanma
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c67f739-3878-48ad-806c-b2ce0d6733a0
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6516f5da83a4133451d73fc10a76a691a931d3ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="using-procedural-activities"></a>Yordam etkinlikleri kullanma
Örnek kullanır <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.Assign>, <xref:System.Activities.Statements.If>, <xref:System.Activities.Statements.While>, <xref:System.Activities.Statements.Switch%601>, <xref:System.Activities.Statements.TryCatch>, ve <xref:System.Activities.Statements.WriteLine> bir tahmin uygulamak için etkinlikler oyun. Rastgele bir sayı tahmin eden oyun seçer ve bu sayıyı tahmin etmeye player sahiptir. Player yanlış tahmin gönderdiğinde, iş akışı yüksek tahmin ya da daha düşük bir ipucu sağlar. Player sayı değerinden 7 girişimlerinde tahminde bulunursa, bir özel Tebrikler kullanıcıya görüntülenir.  
  
## <a name="custom-activities-in-this-sample"></a>Bu örnek özel etkinlikleri  
  
### <a name="readline"></a>ReadLine  
 Metin satırının konsoldan okur. Bu etkinlik türetilen <xref:System.Activities.NativeActivity> sınıfı ve bir satır okunduğunda konsol uygulaması tarafından sürdürüldü bir yer işareti oluşturur.  
  
### <a name="promptint"></a>PromptInt  
 Kullanıcıdan bir sayı yazın ve ardından bir konsol penceresinden okur. Etkinlik türetilen <xref:System.Activities.Activity%601> ve kullandığı <xref:System.Activities.Statements.WriteLine> ve `ReadLine` etkinlikler.  
  
##### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], GuessingGame.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Procedurals`