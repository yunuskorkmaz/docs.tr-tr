---
title: XAML’den Yükleme
ms.date: 03/30/2017
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
ms.openlocfilehash: c46c9020f07731d3d833332d77fd46a162ccb6dc
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715959"
---
# <a name="load-from-xaml"></a>XAML’den Yükleme
Bu örnek, XamlBuildTask aracını çalıştırmak zorunda kalmadan bir XAML iş akışını dinamik olarak yüklemeyi gösterir. Bunun yerine, örnek <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> yöntemini çağırır. Örnek, <xref:System.Activities.XamlIntegration.ActivityXamlServices> sınıfını kullanarak XAML iş akışlarını yükleyen ve bunları yürüten bir Windows Presentation Foundation (WPF) istemci uygulamasıdır. <xref:System.Activities.XamlIntegration.ActivityXamlServices> sınıfı kullanılarak yüklendikten sonra yürütülebilecek bir <xref:System.Activities.DynamicActivity%601> döndürülür.

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2010 kullanarak LoadFromXAML. sln çözüm dosyasını açın.

2. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

3. Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`
