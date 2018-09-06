---
title: Yordam etkinlikleri kullanma
ms.date: 03/30/2017
ms.assetid: 1c67f739-3878-48ad-806c-b2ce0d6733a0
ms.openlocfilehash: bd83f1a0fa9f3af7c22cee73fbc4f984a9ebf53c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43804784"
---
# <a name="using-procedural-activities"></a>Yordam etkinlikleri kullanma
Örnek kullanır <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.Assign>, <xref:System.Activities.Statements.If>, <xref:System.Activities.Statements.While>, <xref:System.Activities.Statements.Switch%601>, <xref:System.Activities.Statements.TryCatch>, ve <xref:System.Activities.Statements.WriteLine> bir tahmin uygulamak için etkinlikleri oyun. Tahmin eden oyun rastgele bir sayı seçer ve bu sayıyı tahmin oyuncusu içeriyor. Oyuncu bir yanlış tahmin gönderdiğinde, iş akışını tahmin daha yüksek veya daha düşük bir ipucu sağlar. Yürütücü numarası 7'den az girişimlerinde tahminler, kullanıcıya özel Tebrikler görüntülenir.  
  
## <a name="custom-activities-in-this-sample"></a>Bu örnekte özel etkinlikler  
  
### <a name="readline"></a>ReadLine  
 Bir metin satırı konsolundan okur. Bu etkinlik türetildiği <xref:System.Activities.NativeActivity> sınıfı ve bir satırı okumak, konsol uygulaması tarafından sürdürüldü bir yer işareti oluşturur.  
  
### <a name="promptint"></a>PromptInt  
 Kullanıcıdan bir sayı yazın ve ardından konsol penceresinden okur. Etkinlik türetildiği <xref:System.Activities.Activity%601> ve kullandığı <xref:System.Activities.Statements.WriteLine> ve `ReadLine` etkinlikler.  
  
##### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], GuessingGame.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Procedurals`