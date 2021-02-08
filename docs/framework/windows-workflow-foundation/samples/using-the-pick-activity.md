---
description: 'Hakkında daha fazla bilgi edinin: çekme etkinliğini kullanma'
title: Pick Etkinliği Kullanma
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 3c7a96c6250db8b9301dfeba858568d5638a29f1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787753"
---
# <a name="using-the-pick-activity"></a>Pick Etkinliği Kullanma

Bu örnek, etkinliğin nasıl kullanılacağını gösterir <xref:System.Activities.Statements.Pick> .

 <xref:System.Activities.Statements.Pick>Etkinlik, olay tabanlı denetim modelleme sağlar. `switch`Deyimdeki dallardan yalnızca birini yürüten C# ifadesiyle benzer şekilde davranır `switch` . Bir `switch` dalın bir değere göre yürütüldüğü deyimin aksine, <xref:System.Activities.Statements.Pick> etkinlik bir etkinliğin nasıl tamamlantığını temel alarak bir dalı yürütür.

 Bu örnek, bir kullanıcının belirli bir süre içinde konsola kendi adını yazmayı ister. <xref:System.Activities.Statements.Pick>Örnekteki etkinliğin, kullanıcının adında 5 saniye içinde olup olmadığına bağlı olarak yürütülen iki dalı vardır. Kullanıcı adlarını 5 saniye içinde yazdığında, ilk dal yürütülür ve özel bir `ReadLine` etkinlik içerir; Aksi takdirde, bir etkinlik içeren diğer dal yürütülür <xref:System.Activities.Statements.Delay> . Konsola bir kullanıcının adı yazıldığında, kullanıcının adı konsolunda yazdırılır. Bir giriş 5 saniye içinde girilmezse, işlem zaman aşımına uğrar.

## <a name="demonstrates"></a>Gösteriler

 <xref:System.Activities.Statements.Pick> etkinlik.

## <a name="discussion"></a>Tartışma

 Örnek, tasarımcı iş akışını ve kodlanmış iş akışını içerir.

 Tasarımcı Iş akışı Örneğin tasarımcı sürümü, tasarımcıda bir iş akışının nasıl oluşturulacağını gösterir. Aşağıdaki dosyalar dahil edilmiştir:

- Program.cs: `Main` örnek iş akışını yürüten Işlevi içerir.

- ReadString.cs: konsolundan bazı girişleri okuyan özel bir etkinlik.

- Sequence1. xaml: seçimi kullanan Tasarımcı kullanılarak oluşturulan bir iş akışı.

 Kodlanmış Iş akışı Örneğin kodlanmış sürümü, tasarımcıda bir iş akışının nasıl oluşturulacağını gösterir. Aşağıdaki dosyalar dahil edilmiştir:

- Program.cs: `Main` örnek iş akışını yürüten Işlevi içerir.

- ReadString.cs: konsolundan bazı girişleri okuyan özel bir etkinlik.

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2010 kullanarak, pick. sln çözüm dosyasını açın.

2. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

3. Çözümü çalıştırmak için F5 'e basın.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`
