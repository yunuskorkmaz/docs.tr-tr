---
ms.openlocfilehash: dd7d3e445772e4b5ec148576ccd1374d56e251bd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614786"
---
### <a name="deadlock-may-result-when-using-reentrant-services"></a>Yer elde edilen hizmetler kullanılırken kilitlenme oluşabilir

#### <a name="details"></a>Ayrıntılar

Bir kilitlenme, hizmet örneklerini aynı anda bir yürütme iş parçacığına kısıtlayan bir tekrar hizmet ile sonuçlanabilir. Bu sorunla karşılaşacağınız hizmetler, kodunda aşağıdaki gibi olacaktır <xref:System.ServiceModel.ServiceBehaviorAttribute> :

```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]
```

#### <a name="suggestion"></a>Öneri

Bu sorunu gidermek için aşağıdakileri yapabilirsiniz:

- Hizmetin eşzamanlılık modunu <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> veya &lt; System. ServiceModel. ConcurrencyMode. Multiple? DisplayProperty = nameWithType olarak ayarlayın &gt; . Örneğin:

```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]
```

- En son güncelleştirmeyi .NET Framework 4.6.2 veya .NET Framework daha sonraki bir sürüme yükseltin. Bu, içindeki akışını devre dışı <xref:System.Threading.ExecutionContext> bırakır <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> . Bu davranış yapılandırılabilir; yapılandırma dosyanıza aşağıdaki uygulama ayarı eklenerek eşdeğerdir:

```xml
<appSettings>
  <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="true" />
</appSettings>
```

Değeri, tekrar eden `Switch.System.ServiceModel.DisableOperationContextAsyncFlow` Hizmetler için hiçbir şekilde ayarlanmamalıdır `false` .

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4.6.2       |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ConcurrencyMode.Reentrant?displayProperty=nameWithType>
