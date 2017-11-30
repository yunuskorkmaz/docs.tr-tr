---
title: Yerel Kanal
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dee09b8f7b1e48a84fa79381d44fe48a4da16129
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="local-channel"></a>Yerel Kanal
Yerel kanal bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aynı uygulama etki alanı içinde iletişim için kullanılan taşıma kanalı. Burada istemci ve hizmet aynı uygulama etki alanında çalışan ve tipik WCF kanalı yığınının (seri hale getirme ve seri durumdan çıkarma iletilerinin) ek yükünü kaçınılmalıdır senaryoları için kullanışlıdır.  
  
## <a name="demonstrates"></a>Gösteriler  
 Yerel Kanal  
  
## <a name="discussion"></a>Tartışma  
 Örnek iki proje dosyaları içerir:  
  
-   **LocalChannel**: geçerli uygulama etki alanı içinde yerel kanal programlı gösterimi. Bu projede gönderen bileşeni ileti bir bellek içi sıraya koyar ve alıcı bileşen alması iletiyi kuyruktan.  
  
-   **ClientAndService**: Bu proje bir hizmeti bir konsol uygulamasında barındırır ve aynı uygulama etki alanı içinde hizmetinden çağırmak için bir istemci çalıştırır.  
  
 Yerel kanal tasarım kanal yığını ve hızını artırmak için seri hale getirme işlemi atlanıyor. Yerel taşıma kanalı, bir kuyruk hizmeti için istemci hizmeti çağrıları taşıma ve istemciye geri dönüş değeri kullanılarak uygulanır. Parametreler ve dönüş değerleri serileştirme yerine örnek nesneleri kopyalar.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Derleme ve LocalChannel çözümü çalıştırın.  
  
2.  Hizmet ana bilgisayarı başlatılır ve istemcinin yerel kanal kullanarak hizmetini çağırır. Hizmet arama sonuçlarını görüntülemek için bir konsol penceresi görünür.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
