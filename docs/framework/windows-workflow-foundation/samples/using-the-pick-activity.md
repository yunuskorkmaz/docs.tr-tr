---
title: Pick Etkinliği Kullanma
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 7ca4527cc1d5bc90ed1ec4df3eef6cf2d8b93b4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142621"
---
# <a name="using-the-pick-activity"></a>Pick Etkinliği Kullanma
Bu örnek, etkinliğin nasıl <xref:System.Activities.Statements.Pick> kullanılacağını gösterir.

 Etkinlik <xref:System.Activities.Statements.Pick> olay tabanlı denetim modellemesi sağlar. İfadedeki dallardan yalnızca birini `switch` çalıştıran C# deyimine benzer `switch` şekilde direnir. Bir `switch` dalın bir değere bağlı olarak yürütüldettiği ifadeden <xref:System.Activities.Statements.Pick> farklı olarak, etkinlik bir etkinliğin nasıl tamamlandığına bağlı olarak bir dalı yürütür.

 Bu örnek, bir kullanıcıdan belirli bir süre içinde konsola kendi adını yazmasını ister. Örnekteki etkinlik, <xref:System.Activities.Statements.Pick> kullanıcının 5 saniye içinde kendi adına tip yapıp yapmamaya bağlı olarak yürütülen iki dala sahiptir. Kullanıcı 5 saniye içinde kendi adına tiplerse, ilk dal `ReadLine` yürütülür ve bu da özel bir etkinlik içerir; aksi takdirde diğer dal yürütülür, bir <xref:System.Activities.Statements.Delay> etkinlik içerir. Konsola bir kullanıcının adı yazıldıktan sonra, kullanıcının adı konsola yazdırılır. Bir giriş 5 saniye içinde girmezse, işlem zaman lanır.

## <a name="demonstrates"></a>Gösteriler
 <xref:System.Activities.Statements.Pick>Etkinlik.

## <a name="discussion"></a>Tartışma
 Örnek, Tasarımcı iş akışı ve kodlanmış iş akışı içerir.

 Tasarımcı İş Akışı Örneğin Tasarımcı sürümü, tasarımcıda nasıl bir iş akışı oluşturulacak larını gösterir. Aşağıdaki dosyalar dahildir:

- Program.cs : `Main` Örnek iş akışını yürüten işlevi içerir.

- ReadString.cs: Konsoldan bazı girdileri okuyan özel bir etkinlik.

- Sequence1.xaml: Pick kullanan tasarımcı kullanılarak oluşturulan bir iş akışı.

 Kodlanmış İş Akışı Örneğin kodlanmış sürümü, tasarımcıda nasıl bir iş akışı oluşturulacak larını gösterir. Aşağıdaki dosyalar dahildir:

- Program.cs : `Main` Örnek iş akışını yürüten işlevi içerir.

- ReadString.cs: Konsoldan bazı girdileri okuyan özel bir etkinlik.

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2010'u kullanarak Pick.sln çözüm dosyasını açın.

2. Çözümü oluşturmak için CTRL+SHIFT+B tuşuna basın.

3. Çözümü çalıştırmak için F5 tuşuna basın.

> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`
