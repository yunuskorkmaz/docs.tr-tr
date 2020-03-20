---
title: XAML’den Yükleme
ms.date: 03/30/2017
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
ms.openlocfilehash: d07ddef8fb982aa0bf707cb688cd23f04bb231d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142725"
---
# <a name="load-from-xaml"></a>XAML’den Yükleme
Bu örnek, XamlBuildTask aracını çalıştırmak zorunda kalmadan bir XAML iş akışının dinamik olarak nasıl yüklenir olduğunu gösterir. Bunun yerine, örnek <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> yöntemi çağırır. Örnek, <xref:System.Activities.XamlIntegration.ActivityXamlServices> sınıfı kullanarak XAML iş akışlarını yükleyen ve bunları yürüten bir Windows Presentation Foundation (WPF) istemci uygulamasıdır. <xref:System.Activities.XamlIntegration.ActivityXamlServices> Sınıf kullanılarak yüklendikten sonra, <xref:System.Activities.DynamicActivity%601> yürütülebilecek bir döndürülür.

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2010'u kullanarak LoadFromXAML.sln çözüm dosyasını açın.

2. Çözümü oluşturmak için CTRL+SHIFT+B tuşuna basın.

3. Çözümü çalıştırmak için CTRL+F5 tuşuna basın.

> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`
