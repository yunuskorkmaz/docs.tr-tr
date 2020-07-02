---
ms.openlocfilehash: 2d0798917b639bc90bf3f78f6fb9f19d0eaf2c71
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614815"
---
### <a name="incorrect-implementation-of-memberdescriptorequals"></a>MemberDescriptor. Equals için yanlış uygulama

#### <a name="details"></a>Ayrıntılar

Yöntemin orijinal uygulanması <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> karşılaştırılan nesnelerden iki farklı dize özelliklerini karşılaştırır: Kategori adı ve açıklama dizesi. Bu çözüm, <xref:System.ComponentModel.MemberDescriptor.Category> birinci nesnenin <xref:System.ComponentModel.MemberDescriptor.Category> ikincisini ikinci bir ile ve <xref:System.ComponentModel.MemberDescriptor.Description> <xref:System.ComponentModel.MemberDescriptor.Description> ikincinin birincisini karşılaştırmaktır.

#### <a name="suggestion"></a>Öneri

Uygulamanız <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> bazen tanımlayıcılar eşdeğer olduğunda geri dönmesine bağımlıysa `false` ve .NET Framework 4.6.2 veya üzerini hedefliyorsanız, birkaç seçeneğiniz vardır:

- <xref:System.ComponentModel.MemberDescriptor.Category> <xref:System.ComponentModel.MemberDescriptor.Description> Yöntemini çağırmaya ek olarak ve alanlarını el ile karşılaştırmak için kod değişiklikleri yapın <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> .
- app.config dosyasına aşağıdaki değeri ekleyerek bu değişikliği geri çevirin:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true" />
</runtime>
```

Uygulamanız .NET Framework 4.6.1 veya daha önceki bir sürümü hedefliyorsa ve .NET Framework 4.6.2 ya da üzerinde çalışıyorsa ve bu değişikliği etkinleştirmek istiyorsanız, `false` app.config dosyasına aşağıdaki değeri ekleyerek uyumluluk anahtarını olarak ayarlayabilirsiniz:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=false" />
</runtime>
```

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4.6.2       |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.ComponentModel.MemberDescriptor.Equals(System.Object)?displayProperty=nameWithType>
