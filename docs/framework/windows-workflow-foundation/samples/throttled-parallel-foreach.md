---
title: Kısıtlanmış paralel ForEach
ms.date: 03/30/2017
ms.assetid: f2855b5f-e9a7-433d-96a4-40fc31025215
ms.openlocfilehash: 8691edb8a5a61204b187be8def553f2f06be0f0d
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48581868"
---
# <a name="throttled-parallel-foreach"></a>Kısıtlanmış paralel ForEach
`ThrottleParallelForEach` Etkinlik benzer <!--zz <xref:System.Activities.Statements.ParallelForEach>--> `System.Activities.Statements.ParallelForEach` etkinliği ile bir özel durum olan ayarlamaya olanak tanır eşzamanlılık faktörü yürütmek için eşzamanlı dalların sayısını sınırlamak için. `ThrottleParallelForEach` Etkinlik türetilir <xref:System.Activities.NativeActivity>, diğer etkinlikleri (alt) zamanlamak gereken ve bu yalnızca üzerinden erişilebilir olduğundan <xref:System.Activities.NativeActivityContext> sınıfı.

## <a name="projects"></a>Projeler

|**projectName**|**Açıklama**|**Ana dosyaları**|
|-|-|-|
|ThrottledParallelForEach|İçeren `ThrottledParallelForEach` etkinlik ve iş Tasarımcısı.|ThrottledParallelForEach.cs<br /><br /> `ThrottledParallelForEach` Etkinlik tanımı.|
|CodeTestClient|Örnek, yapılandırır ve bir iş akışı ile çalışan istemci uygulama bir `ThrottledParallelForEach` kesin kod kullanarak.|Program.cs<br /><br /> Örnek iş akışı örneğini çalıştıran ve tanımlar.|

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1.  Visual Studio 2010'u kullanarak, ThrottledParallelForEach.sln dosyasını açın.

2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

3.  Çözümü çalıştırmak için F5 tuşuna basın.

> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\ThrottledParallelForEach`