---
ms.openlocfilehash: 519de92ca4201d199941afe6382ddf9fc480fbbd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614775"
---
### <a name="servicebase-doesnt-propagate-onstart-exceptions"></a>ServiceBase, OnStart özel durumlarını yaymıyor

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,7 ve önceki sürümlerde, hizmet başlangıcında oluşturulan özel durumlar, çağıranına yayılmaz <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> .<br/>.NET Framework 4.7.1 ' i hedefleyen uygulamalarla başlayarak, çalışma zamanı, <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> başlatılamaz hizmetler için özel durumları yayar.

#### <a name="suggestion"></a>Öneri

Hizmet başlangıcı ' nde, bir özel durum varsa, bu özel durum yayılacaktır. Bu, hizmetlerin başlayaamadığı durumların tanılanmasına yardımcı olur. <br/>Bu davranış istenmeyen ise, &lt; &gt; &lt; uygulama yapılandırma dosyanızın çalışma zamanı bölümüne aşağıdaki AppContextSwitchOverrides öğesini ekleyerek devre dışı bırakabilirsiniz &gt; :

```xml
<AppContextSwitchOverrides value="Switch.System.ServiceProcess.DontThrowExceptionsOnStart=true" />
```

Uygulamanız 4.7.1 sürümünden önceki bir sürümü hedefliyorsa ancak bu davranışa sahip olmak istiyorsanız, &lt; &gt; &lt; uygulama yapılandırma dosyanızın Runtime bölümüne aşağıdaki AppContextSwitchOverrides öğesini ekleyin &gt; :

```xml
<AppContextSwitchOverrides value="Switch.System.ServiceProcess.DontThrowExceptionsOnStart=false" />
```

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4.7.1       |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase)?displayProperty=nameWithType>
- <xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase[])?displayProperty=nameWithType>
