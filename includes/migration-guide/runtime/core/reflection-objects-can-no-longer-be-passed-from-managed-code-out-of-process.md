---
ms.openlocfilehash: a54b17b2002bd0f85b8b47c5e37e040470d6c494
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621435"
---
### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a>Yansıma nesneleri artık yönetilen koddan işlem dışı DCOM istemcilerine geçirilemez

#### <a name="details"></a>Ayrıntılar

Yansıma nesneleri artık yönetilen koddan işlem dışı DCOM istemcilerine geçirilemez. Aşağıdaki türler etkilenir:<ul><li><xref:System.Reflection.Assembly?displayProperty=fullName></li><li><xref:System.Reflection.MemberInfo?displayProperty=fullName>(ve,,, ve dahil olmak üzere türetilmiş türleri <xref:System.Reflection.FieldInfo?displayProperty=fullName> <xref:System.Reflection.MethodInfo?displayProperty=fullName> <xref:System.Type?displayProperty=fullName> <xref:System.Reflection.TypeInfo?displayProperty=fullName> )</li><li><xref:System.Reflection.MethodBody?displayProperty=fullName></li><li><xref:System.Reflection.Module?displayProperty=fullName></li><li><xref:System.Reflection.ParameterInfo?displayProperty=fullName>.</li></ul><code>IMarshal</code>Nesne dönüşü için öğesine çağrılar <code>E_NOINTERFACE</code> .

#### <a name="suggestion"></a>Öneri

Yansıtma olmayan nesnelerle çalışacak sıralama kodunu Güncelleştir

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4.6|
|Tür|Çalışma Zamanı|
