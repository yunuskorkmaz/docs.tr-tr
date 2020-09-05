---
ms.openlocfilehash: f61cf21f9f30662cc8e383bb3aeb5c642f1665b8
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497843"
---
### <a name="deadlock-may-result-when-using-reentrant-services"></a>Yer elde edilen hizmetler kullanılırken kilitlenme oluşabilir

#### <a name="details"></a>Ayrıntılar

Bir kilitlenme, hizmet örneklerini aynı anda bir yürütme iş parçacığına kısıtlayan bir tekrar hizmet ile sonuçlanabilir. Bu sorunla karşılaşacağınız hizmetler, kodunda aşağıdaki gibi olacaktır <xref:System.ServiceModel.ServiceBehaviorAttribute> :

```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]
```

#### <a name="suggestion"></a>Öneri

Bu sorunu gidermek için aşağıdakileri yapabilirsiniz:

- Hizmetin eşzamanlılık modunu veya olarak ayarlayın <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> <xref:System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType> . Örneğin:

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
