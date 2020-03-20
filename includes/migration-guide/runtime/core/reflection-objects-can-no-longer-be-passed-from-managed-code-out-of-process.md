---
ms.openlocfilehash: 38c774417fc94fa080bf2b82c04d575e9068cdcb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858579"
---
### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a>Yansıma nesneleri artık yönetilen koddan işlem dışı DCOM istemcilerine geçirilemez

|   |   |
|---|---|
|Ayrıntılar|Yansıma nesneleri artık yönetilen koddan işlem dışı DCOM istemcilerine geçirilemez. Aşağıdaki türleri etkilenir:<ul><li><xref:System.Reflection.Assembly?displayProperty=name></li><li><xref:System.Reflection.MemberInfo?displayProperty=name>(ve türetilmiş türleri, <xref:System.Reflection.FieldInfo?displayProperty=name>dahil olmak üzere , <xref:System.Reflection.MethodInfo?displayProperty=name> <xref:System.Type?displayProperty=name>, , ve <xref:System.Reflection.TypeInfo?displayProperty=name>)</li><li><xref:System.Reflection.MethodBody?displayProperty=name></li><li><xref:System.Reflection.Module?displayProperty=name></li><li><xref:System.Reflection.ParameterInfo?displayProperty=name>.</li></ul>Nesne <code>IMarshal</code> nin iadesi <code>E_NOINTERFACE</code>için çağrılar.|
|Öneri|Yansıma yanlamayan nesnelerle çalışmak için kod lama güncelleştirme|
|Kapsam|İkincil|
|Sürüm|4.6|
|Tür|Çalışma Zamanı|
