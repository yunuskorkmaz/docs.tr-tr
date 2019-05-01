---
ms.openlocfilehash: 38c774417fc94fa080bf2b82c04d575e9068cdcb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664545"
---
### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a>Yansıma nesneleri artık yönetilen koddan işlem dışı DCOM istemcilere geçirilebilir

|   |   |
|---|---|
|Ayrıntılar|Yansıma nesneleri artık işlem dışı DCOM istemcilere yönetilen koddan geçirilebilir. Aşağıdaki türleri etkilenir:<ul><li><xref:System.Reflection.Assembly?displayProperty=name></li><li><xref:System.Reflection.MemberInfo?displayProperty=name> (ve onun türetilmiş türlerine dahil olmak üzere <xref:System.Reflection.FieldInfo?displayProperty=name>, <xref:System.Reflection.MethodInfo?displayProperty=name>, <xref:System.Type?displayProperty=name>, ve <xref:System.Reflection.TypeInfo?displayProperty=name>)</li><li><xref:System.Reflection.MethodBody?displayProperty=name></li><li><xref:System.Reflection.Module?displayProperty=name></li><li><xref:System.Reflection.ParameterInfo?displayProperty=name>.</li></ul>Çağrılar <code>IMarshal</code> nesnenin dönüş <code>E_NOINTERFACE</code>.|
|Öneri|Yansıma olmayan nesnelerle çalışmayı sıralama kodu güncelleştirme|
|Kapsam|İkincil|
|Sürüm|4.6|
|Tür|Çalışma zamanı|
