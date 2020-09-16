---
title: Tür eşdeğerliği ve katıştırılmış birlikte çalışma türleri
description: Yönetilen bir derleme ve bu derlemeye gömülü COM türleri arasında .NET türleri ve üyeleri arasında tür eşdeğerliği anlayın. .NET 4 ve üzeri için.
ms.date: 03/30/2017
helpviewer_keywords:
- type equivalence
- embedded interop types
- primary interop assemblies,not necessary in CLR version 4
- NoPIA
ms.assetid: 78892eba-2a58-4165-b4b1-0250ee2f41dc
ms.openlocfilehash: a096c6bd0703c19c6049ad5ab2532b4b05f6ede0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558829"
---
# <a name="type-equivalence-and-embedded-interop-types"></a>Tür eşdeğerliği ve katıştırılmış birlikte çalışma türleri

.NET Framework 4 ' ten başlayarak, ortak dil çalışma zamanı, yönetilen derlemelerin, birlikte çalışabilirlik derlemelerinden COM türleri için tür bilgilerini almasını gerektirmek yerine, COM türleri için tür bilgilerini doğrudan yönetilen derlemelere katıştırmayı destekler. Gömülü tür bilgileri yalnızca yönetilen bir derleme tarafından gerçekten kullanılan türleri ve üyeleri içerdiğinden, iki yönetilen derleme aynı COM türünde çok farklı görünümlere sahip olabilir. Her yönetilen derlemenin, <xref:System.Type> com türünün görünümünü temsil eden farklı bir nesnesi vardır. Ortak dil çalışma zamanı, arabirimler, yapılar, numaralandırmalar ve temsilciler için bu farklı görünümler arasında tür eşdeğerliği destekler.

Tür eşdeğerliği, yönetilen bir derlemeden diğerine geçirilen bir COM nesnesinin, alıcı derlemede uygun yönetilen türe yayınlanmasını anlamına gelir.

> [!NOTE]
> Tür denklik ve katıştırılmış birlikte çalışma türleri, uygulamalarla birlikte çalışma derlemeleri dağıtmak gerekli olmadığı için COM bileşenlerini kullanan uygulamaların ve eklentilerin dağıtımını basitleştirir. Paylaşılan COM bileşenlerinden oluşan geliştiricilerin, bileşenlerinin önceki .NET Framework sürümleri tarafından kullanılmasını istiyorsanız birincil birlikte çalışma derlemeleri (PIA 'lar) oluşturması gerekir.

## <a name="type-equivalence"></a>Tür denklik

 Arabirimler, yapılar, numaralandırmalar ve temsilciler için COM türlerinin denklik 'i desteklenir. Aşağıdaki koşulların tümü doğruysa COM türleri eşdeğer olarak niteler:

- Türler hem arabirimlerdir, hem de her iki yapı veya her ikisi de temsilcisdir.

- Türler, sonraki bölümde açıklandığı gibi aynı kimliğe sahiptir.

- Her iki tür de, tür denklik [IÇIN com türlerini işaretleme](#marking-com-types-for-type-equivalence) bölümünde açıklandığı gibi tür denklik için uygundur.

### <a name="type-identity"></a>Tür kimliği

İki tür, kapsamları ve kimlikleri eşleşiyorsa aynı kimliğe sahip olacak şekilde belirlenir, diğer bir deyişle, her birinin <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> özniteliği varsa ve iki özniteliğin eşleşen <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> ve <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> özellikleri vardır. İçin karşılaştırma <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> büyük/küçük harfe duyarlıdır.

Bir türün <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> özniteliği yoksa veya <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> kapsam ve tanımlayıcı belirtmeyen bir özniteliği varsa, tür şu şekilde denklik için de kabul edilebilir:

- Arabirimler için, özelliği yerine öğesinin değeri <xref:System.Runtime.InteropServices.GuidAttribute> kullanılır <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A?displayProperty=nameWithType> ve özelliği <xref:System.Type.FullName%2A?displayProperty=nameWithType> (diğer bir deyişle, ad alanı dahil olmak üzere tür adı), özelliği yerine kullanılır <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A?displayProperty=nameWithType> .

- Yapılar, numaralandırmalar ve temsilciler için, <xref:System.Runtime.InteropServices.GuidAttribute> kapsayan derlemenin özelliği yerine kullanılır ve özelliği özelliği <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> <xref:System.Type.FullName%2A?displayProperty=nameWithType> yerine kullanılır <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> .

### <a name="marking-com-types-for-type-equivalence"></a>Tür denklik için COM türleri işaretleniyor

 Tür denklik için uygun bir türü iki şekilde işaretleyebilirsiniz:

- <xref:System.Runtime.InteropServices.TypeIdentifierAttribute>Özniteliği türüne uygulayın.

- Türü bir COM içeri aktarma türü yapın. Bir arabirim, özniteliği varsa COM içeri aktarma türüdür <xref:System.Runtime.InteropServices.ComImportAttribute> . Arabirim, yapı, numaralandırma veya temsilci, tanımlanan derlemenin özniteliği varsa COM içeri aktarma türüdür <xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute> .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Type.IsEquivalentTo%2A>
- [Yönetilen kodda COM türlerini kullanma](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))
- [Tür Kitaplığını Derleme Olarak İçeri Aktarma](importing-a-type-library-as-an-assembly.md)
