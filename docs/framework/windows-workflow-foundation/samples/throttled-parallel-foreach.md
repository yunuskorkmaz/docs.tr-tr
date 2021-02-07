---
description: 'Daha fazla bilgi edinin: kısıtlanmış paralel ForEach'
title: Kısıtlanmış Paralel ForEach
ms.date: 03/30/2017
ms.assetid: f2855b5f-e9a7-433d-96a4-40fc31025215
ms.openlocfilehash: 2c1d1386f0b8c5b3c68d60bc83386ccfdf5e7875
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741685"
---
# <a name="throttled-parallel-foreach"></a>Kısıtlanmış Paralel ForEach

`ThrottleParallelForEach`Etkinlik, <xref:System.Activities.Statements.ParallelForEach%601> eşzamanlı dalların yürütülmesi için eşzamanlılık faktörünün ayarlanmasına izin veren bir özel durumla etkinlik ile benzerdir. `ThrottleParallelForEach`Etkinliğin <xref:System.Activities.NativeActivity> , diğer etkinlikleri (alt etkinlikler) zamanlaması gerektiğinden ve bu, yalnızca sınıfı aracılığıyla erişilebilir olduğundan, öğesinden türetilir <xref:System.Activities.NativeActivityContext> .

## <a name="projects"></a>Projeler

|**ProjectName**|**Açıklama**|**Ana dosyalar**|
|-|-|-|
|Bir azaltıcı ParallelForEach|`ThrottledParallelForEach`Etkinlik ve tasarımcısını içerir.|ThrottledParallelForEach.cs<br /><br /> `ThrottledParallelForEach`Etkinlik tanımı.|
|Codetekstclient|Bir iş akışını yapılandıran ve bu örnek bir kod kullanarak çalıştıran örnek istemci uygulaması `ThrottledParallelForEach` .|Program.cs<br /><br /> Örnek iş akışının bir örneğini tanımlar ve çalıştırır.|

## <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2010 kullanarak, Kısıtledparallelforeach. sln dosyasını açın.

2. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

3. Çözümü çalıştırmak için F5 'e basın.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\ThrottledParallelForEach`
