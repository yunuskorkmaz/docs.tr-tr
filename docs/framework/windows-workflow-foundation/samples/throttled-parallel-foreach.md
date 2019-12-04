---
title: Kısıtlanmış Paralel ForEach
ms.date: 03/30/2017
ms.assetid: f2855b5f-e9a7-433d-96a4-40fc31025215
ms.openlocfilehash: 340e4ff154b63221ec911c872a1154bdb672cf8c
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715915"
---
# <a name="throttled-parallel-foreach"></a>Kısıtlanmış Paralel ForEach

`ThrottleParallelForEach` etkinliği, eş zamanlı dalların yürütülmesi için eşzamanlılık faktörünün ayarlanmasına izin veren bir özel durumla <xref:System.Activities.Statements.ParallelForEach%601> etkinliğe benzer. `ThrottleParallelForEach` etkinliği, diğer etkinlikleri (alt etkinlikler) zamanlaması gerektiğinden ve bu yalnızca <xref:System.Activities.NativeActivityContext> sınıfı aracılığıyla erişilebilir olduğu için <xref:System.Activities.NativeActivity>türetilir.

## <a name="projects"></a>Projeler

|**ProjectName**|**Açıklama**|**Ana dosyalar**|
|-|-|-|
|Bir azaltıcı ParallelForEach|`ThrottledParallelForEach` etkinliği ve tasarımcısını içerir.|ThrottledParallelForEach.cs<br /><br /> `ThrottledParallelForEach` etkinlik tanımı.|
|Codetekstclient|Zorunlu kod kullanarak bir `ThrottledParallelForEach` iş akışı yapılandıran ve çalıştıran örnek istemci uygulaması.|Program.cs<br /><br /> Örnek iş akışının bir örneğini tanımlar ve çalıştırır.|

## <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2010 kullanarak, Kısıtledparallelforeach. sln dosyasını açın.

2. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

3. Çözümü çalıştırmak için F5 'e basın.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\ThrottledParallelForEach`
