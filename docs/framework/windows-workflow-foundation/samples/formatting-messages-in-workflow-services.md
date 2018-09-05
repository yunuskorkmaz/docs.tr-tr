---
title: İş akışı hizmetlerinde iletileri biçimlendirme
ms.date: 03/30/2017
ms.assetid: 6d15d44b-20f8-4cb7-bd4f-598c32781ebc
ms.openlocfilehash: eb9a6b3a83a28154dc968bd4c1c41d34028bdd41
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43562923"
---
# <a name="formatting-messages-in-workflow-services"></a>İş akışı hizmetlerinde iletileri biçimlendirme
Bu örnek nasıl farklı kullanıcı türleri kullanılabilir Mesajlaşma etkinlikleri (WF Hizmetleri) gösterir. Örnek hizmet basit gider onay hizmetidir ve üç işlemini kullanıma sunar. `ApproveExpense` bir veri anlaşması türü alır ve bilinen türleri kullanmayı gösterir. İşlem döndürür `true` veya `false` gider tutarını temel. `ApprovePO` XmlSerializer türü alır ve döndürür `true` veya `false` gider tutarını temel.`ApprovedVendor` bir ileti anlaşması türü alır ve döndürür `true` veya `false` satıcı onaylanan satıcıları listesinde değilse veya istek (Finans departmanı, herhangi bir satıcı kullanabilirsiniz) Finans departmanında geldiyse.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Proje çözümde yük [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ve projeyi derleyin.  
  
2.  İlk [çözüm temel dizini] \FormatterService\bin\debug\ içinde oluşturulan bir hizmet çalıştırma  
  
3.  İkinci olarak, [çözüm temel dizini] \FormatterClient\bin\debug içinde oluşturulan istemci uygulamasını çalıştırın.  
  
4.  İstemci, üç hizmet işlemleri çağırır ve sonuçları yazdırır. Tamamlandığında, istemci ve hizmet çıkmak için ENTER tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Formatter`