---
ms.openlocfilehash: f011f6ebe0fa85a59f3e69c93bba9eddc4c1689b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496417"
---
### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a>Yansıma nesneleri artık yönetilen koddan işlem dışı DCOM istemcilerine geçirilemez

#### <a name="details"></a>Ayrıntılar

Yansıma nesneleri artık yönetilen koddan işlem dışı DCOM istemcilerine geçirilemez. Aşağıdaki türler etkilenir:

- <xref:System.Reflection.Assembly?displayProperty=fullName>
- <xref:System.Reflection.MemberInfo?displayProperty=fullName> (ve,,, ve dahil olmak üzere türetilmiş türleri <xref:System.Reflection.FieldInfo?displayProperty=fullName> <xref:System.Reflection.MethodInfo?displayProperty=fullName> <xref:System.Type?displayProperty=fullName> <xref:System.Reflection.TypeInfo?displayProperty=fullName> )
- <xref:System.Reflection.MethodBody?displayProperty=fullName>
- <xref:System.Reflection.Module?displayProperty=fullName>
- <xref:System.Reflection.ParameterInfo?displayProperty=fullName>

<code>IMarshal</code>Nesne dönüşü için öğesine çağrılar <code>E_NOINTERFACE</code> .

#### <a name="suggestion"></a>Öneri

Yansıtma olmayan nesnelerle çalışmak için sıralama kodunu güncelleştirin.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4.6|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Reflection.Assembly?displayProperty=fullName>
- <xref:System.Reflection.FieldInfo?displayProperty=fullName>
- <xref:System.Reflection.MemberInfo?displayProperty=fullName>
- <xref:System.Reflection.MethodBody?displayProperty=fullName>
- <xref:System.Reflection.MethodInfo?displayProperty=fullName>
- <xref:System.Reflection.Module?displayProperty=fullName>
- <xref:System.Reflection.ParameterInfo?displayProperty=fullName>
- <xref:System.Reflection.TypeInfo?displayProperty=fullName>
- <xref:System.Type?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Reflection.Assembly`
- `T:System.Reflection.FieldInfo`
- `T:System.Reflection.MemberInfo`
- `T:System.Reflection.MethodBody`
- `T:System.Reflection.MethodInfo`
- `T:System.Reflection.Module`
- `T:System.Reflection.ParameterInfo`
- `T:System.Reflection.TypeInfo`
- `T:System.Type`

-->
