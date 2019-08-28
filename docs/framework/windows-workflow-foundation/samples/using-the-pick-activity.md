---
title: Pick Etkinliği Kullanma
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 03b9ff7f552ad0cdcfbe9c46121a2f46f35de52a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70037875"
---
# <a name="using-the-pick-activity"></a>Pick Etkinliği Kullanma
Bu örnek, <xref:System.Activities.Statements.Pick> etkinliğin nasıl kullanılacağını gösterir.

 Etkinlik <xref:System.Activities.Statements.Pick> , olay tabanlı denetim modelleme sağlar. C# `switch` Deyimdeki`switch` dallardan yalnızca birini yürüten deyimle benzer şekilde davranır. Bir dalın bir değere göre yürütüldüğü <xref:System.Activities.Statements.Pick> deyiminaksine,etkinlikbiretkinliğinnasıltamamlantığınıtemelalarakbirdalıyürütür.`switch`

 Bu örnek, bir kullanıcının belirli bir süre içinde konsola kendi adını yazmayı ister. Örnekteki <xref:System.Activities.Statements.Pick> etkinliğin, kullanıcının adında 5 saniye içinde olup olmadığına bağlı olarak yürütülen iki dalı vardır. Kullanıcı adlarını 5 saniye içinde yazdığında, ilk dal yürütülür ve özel `ReadLine` bir etkinlik içerir; Aksi takdirde, bir <xref:System.Activities.Statements.Delay> etkinlik içeren diğer dal yürütülür. Konsola bir kullanıcının adı yazıldığında, kullanıcının adı konsolunda yazdırılır. Bir giriş 5 saniye içinde girilmezse, işlem zaman aşımına uğrar.

## <a name="demonstrates"></a>Gösteriler
 <xref:System.Activities.Statements.Pick>etkinlik.

## <a name="discussion"></a>Tartışma
 Örnek, tasarımcı iş akışını ve kodlanmış iş akışını içerir.

 Tasarımcı Iş akışı Örneğin tasarımcı sürümü, tasarımcıda bir iş akışının nasıl oluşturulacağını gösterir. Aşağıdaki dosyalar dahil edilmiştir:

- Program.cs: Örnek iş akışını yürüten işleviiçerir.`Main`

- ReadString.cs: Konsolundan bir girişi okuyan özel etkinlik.

- Sequence1. xaml: Seçme kullanan Tasarımcı kullanılarak oluşturulan bir iş akışı.

 Kodlanmış Iş akışı Örneğin kodlanmış sürümü, tasarımcıda bir iş akışının nasıl oluşturulacağını gösterir. Aşağıdaki dosyalar dahil edilmiştir:

- Program.cs: Örnek iş akışını yürüten işleviiçerir.`Main`

- ReadString.cs: Konsolundan bir girişi okuyan özel etkinlik.

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2010 kullanarak, pick. sln çözüm dosyasını açın.

2. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

3. Çözümü çalıştırmak için F5 'e basın.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`
