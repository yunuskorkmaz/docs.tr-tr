---
title: "İş akışı hizmetleri iletilerinde biçimlendirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d15d44b-20f8-4cb7-bd4f-598c32781ebc
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d2367f4fe4ebe576eb9a5e2f707eb043e5ee7ccb
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2017
---
# <a name="formatting-messages-in-workflow-services"></a>İş akışı hizmetleri iletilerinde biçimlendirme
Bu örnek nasıl farklı kullanıcı türleri kullanılabilir Mesajlaşma etkinlikleri (WF Hizmetleri) gösterir. Örnek hizmeti bir basit gider onay hizmetidir ve üç işlemini kullanıma sunar. `ApproveExpense`bir veri sözleşmesi türü alır ve bilinen türleri kullanmayı gösterir. İşlemi döndürür `true` veya `false` gider miktarına bağlı. `ApprovePO`XmlSerializer türü alıp döndüren `true` veya `false` gider miktarına bağlı.`ApprovedVendor` Sözleşme türden bir ileti alıp döndüren `true` veya `false` satıcı onaylanan satıcılar listesinde ise veya istek (Finans departmanı herhangi bir satıcı kullanabilir) Finans departmanından geldiyse.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Proje çözümde yük [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ve projeyi oluşturun.  
  
2.  [Çözüm temel dizin] \FormatterService\bin\debug\ oluşturulan hizmeti, ilk çalıştırma  
  
3.  İkinci olarak, [çözüm temel dizin] \FormatterClient\bin\debug oluşturulan istemci uygulaması çalıştırın.  
  
4.  İstemci, üç işlemi hizmet üzerinde çağırır ve sonuçlarını yazdırır. Tamamlandığında, istemci ve hizmet çıkmak için ENTER tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Formatter`