---
title: Özel Dengeleme örnek
ms.date: 03/30/2017
ms.assetid: 385920da-9284-44bf-9fe9-0d87c7478ec5
ms.openlocfilehash: ac141a48f87f5b14f6b528f7b3ceb7fdddeaf2d2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43475874"
---
# <a name="custom-compensation-sample"></a>Özel Dengeleme örnek
Bu örnek nasıl kullanılacağını gösterir <xref:System.Activities.Statements.CompensableActivity> ve özel telafi mantığı tanımlamak için kendi maaş işleyicisi. Bu örnekte modellenmiş bir Kamyon kiralama kurumu senaryodur.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Benzetimli adımlar şunlardır:  
  
1.  Kullanıcı isteklerinin kiralama teklifleri için belirli bir tarihten kamyon.  
  
2.  Üç kamyon şirketin iletişim kurulur ve üç tırnak sağlanır.  
  
3.  Kullanıcı, tek bir kamyon teklif seçer ve sıralamak için kredi kartı ile devam eder.  
  
4.  Uygulama, diğer iki kamyon tırnak iptal eder.  
  
5.  Uygulamayı iptal 10 gün olursa premium olmayan hesaplar için iade olmayan veya ayırma tarihten önce hizmet için ücret.  
  
6.  Uygulama Kamyon kiralama ücret.  
  
7.  Uygulama, rezervasyon tarihi veya ayırmayı iptal etmek müşteri karar kadar hangisi önce gelirse bekler.  
  
8.  Müşteri ayırmayı iptal ederse <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> özel telafi mantığının göre aşağıdaki mantık çalıştırır:  
  
    1.  Müşteri, bir premium olmayan hesabına sahiptir ve 10 günden önce rezervasyon tarihi ve ardından hizmet ücretinin ise hala ücretlendirilir; Aksi takdirde uygulama, hizmet ücretinin mahsup işlemleri.  
  
    2.  Rest (kamyon sipariş + kamyon siparişi masrafı) compensable etkinliklerinin ters sırada yürütülmesini dengelemek için varsayılan telafi mantığı göre çalıştırın.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], CustomCompensation.sln çözümü açın. Bunu \WF\Basic\Compensation\CustomCompensation dizininde bulunur.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Uygulamayı çalıştırmak için CTRL + F5 tuşlarına basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CustomCompensation`