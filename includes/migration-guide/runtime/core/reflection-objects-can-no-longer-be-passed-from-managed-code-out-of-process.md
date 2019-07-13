---
ms.openlocfilehash: d00f86c492a7d32344b1067a48c8e53aa2a43426
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858579"
---
### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a>Yansıma nesneleri artık yönetilen koddan işlem dışı DCOM istemcilere geçirilebilir

|   |   |
|---|---|
|Ayrıntılar|Yansıma nesneleri artık işlem dışı DCOM istemcilere yönetilen koddan geçirilebilir. Aşağıdaki türleri etkilenir:<ul><li><xref:System.Reflection.Assembly?displayProperty=name></li><li><xref:System.Reflection.MemberInfo?displayProperty=name> (ve onun türetilmiş türlerine dahil olmak üzere <xref:System.Reflection.FieldInfo?displayProperty=name>, <xref:System.Reflection.MethodInfo?displayProperty=name>, <xref:System.Type?displayProperty=name>, ve <xref:System.Reflection.TypeInfo?displayProperty=name>)</li><li><xref:System.Reflection.MethodBody?displayProperty=name></li><li><xref:System.Reflection.Module?displayProperty=name></li><li><xref:System.Reflection.ParameterInfo?displayProperty=name>.</li></ul>Çağrılar <code>IMarshal</code> nesnenin dönüş <code>E_NOINTERFACE</code>.|
|Öneri|Yansıma olmayan nesnelerle çalışmayı sıralama kodu güncelleştirme|
|`Scope`|Küçük|
|Version|4.6|
|Type|Çalışma zamanı|

