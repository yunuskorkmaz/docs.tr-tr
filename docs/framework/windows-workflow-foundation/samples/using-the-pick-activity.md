---
title: Pick Etkinliği Kullanma
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: b0997254615ca962fd386dea70c67a8edb36c90a
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715523"
---
# <a name="using-the-pick-activity"></a>Pick Etkinliği Kullanma
Bu örnek, <xref:System.Activities.Statements.Pick> etkinliğinin nasıl kullanılacağını gösterir.

 <xref:System.Activities.Statements.Pick> etkinliği olay tabanlı denetim modellemesini sağlar. `switch` deyimindeki dallardan yalnızca C# birini yürüten `switch` bildirimine benzer şekilde davranır. Bir dalın bir değere göre yürütüldüğü `switch` deyimin aksine, <xref:System.Activities.Statements.Pick> etkinliği bir etkinliğin nasıl tamamlantığını temel alarak bir dalı yürütür.

 Bu örnek, bir kullanıcının belirli bir süre içinde konsola kendi adını yazmayı ister. Örnekteki <xref:System.Activities.Statements.Pick> etkinliğin, kullanıcının adında 5 saniye içinde olup olmadığına bağlı olarak yürütülen iki dalı vardır. Kullanıcı adlarını 5 saniye içinde yazdığında, ilk dal yürütülür ve özel bir `ReadLine` etkinliği içerir; Aksi takdirde, <xref:System.Activities.Statements.Delay> bir etkinlik içeren diğer dal yürütülür. Konsola bir kullanıcının adı yazıldığında, kullanıcının adı konsolunda yazdırılır. Bir giriş 5 saniye içinde girilmezse, işlem zaman aşımına uğrar.

## <a name="demonstrates"></a>Gösterir
 <xref:System.Activities.Statements.Pick> etkinliği.

## <a name="discussion"></a>Tartışma
 Örnek, tasarımcı iş akışını ve kodlanmış iş akışını içerir.

 Tasarımcı Iş akışı Örneğin tasarımcı sürümü, tasarımcıda bir iş akışının nasıl oluşturulacağını gösterir. Aşağıdaki dosyalar dahil edilmiştir:

- Program.cs: örnek iş akışını yürüten `Main` işlevini Içerir.

- ReadString.cs: konsolundan bazı girişleri okuyan özel bir etkinlik.

- Sequence1. xaml: seçimi kullanan Tasarımcı kullanılarak oluşturulan bir iş akışı.

 Kodlanmış Iş akışı Örneğin kodlanmış sürümü, tasarımcıda bir iş akışının nasıl oluşturulacağını gösterir. Aşağıdaki dosyalar dahil edilmiştir:

- Program.cs: örnek iş akışını yürüten `Main` işlevini Içerir.

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
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`
