---
title: XAML’den Yükleme
ms.date: 03/30/2017
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
ms.openlocfilehash: e0cac1b6dfb9568ba08079cf5194b3432eea856f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637710"
---
# <a name="load-from-xaml"></a>XAML’den Yükleme
Bu örnek nasıl XamlBuildTask aracı çalıştırmak zorunda kalmadan bir XAML iş akışı dinamik olarak yükleneceğini gösterir. Bunun yerine, örnek çağırır <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> yöntemi. Örnek kullanarak XAML iş akışları yükleyen bir Windows Presentation Foundation (WPF) istemci uygulamasıdır <xref:System.Activities.XamlIntegration.ActivityXamlServices> sınıfı ve bunları yürütür. Kullanılarak yüklenmiş sonra <xref:System.Activities.XamlIntegration.ActivityXamlServices> sınıfı, bir <xref:System.Activities.DynamicActivity%601> , yürütülebilir döndürülür.

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2010 kullanarak LoadFromXAML.sln çözüm dosyasını açın.

2. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

3. Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.

> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`
