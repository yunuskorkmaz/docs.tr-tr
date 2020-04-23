---
title: Tür eşdeğerliği ve katıştırılmış birlikte çalışma türleri
ms.date: 03/30/2017
helpviewer_keywords:
- type equivalence
- embedded interop types
- primary interop assemblies,not necessary in CLR version 4
- NoPIA
ms.assetid: 78892eba-2a58-4165-b4b1-0250ee2f41dc
ms.openlocfilehash: ee9d2d94d62f262ef61edc66ce915e1227532d67
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126399"
---
# <a name="type-equivalence-and-embedded-interop-types"></a>Tür eşdeğerliği ve katıştırılmış birlikte çalışma türleri

.NET Framework 4 ' ten başlayarak, ortak dil çalışma zamanı, yönetilen derlemelerin, birlikte çalışabilirlik derlemelerinden COM türleri için tür bilgilerini almasını gerektirmek yerine, COM türleri için tür bilgilerini doğrudan yönetilen derlemelere katıştırmayı destekler. Gömülü tür bilgileri yalnızca yönetilen bir derleme tarafından gerçekten kullanılan türleri ve üyeleri içerdiğinden, iki yönetilen derleme aynı COM türünde çok farklı görünümlere sahip olabilir. Her yönetilen derlemenin, COM türünün <xref:System.Type> görünümünü temsil eden farklı bir nesnesi vardır. Ortak dil çalışma zamanı, arabirimler, yapılar, numaralandırmalar ve temsilciler için bu farklı görünümler arasında tür eşdeğerliği destekler.

Tür eşdeğerliği, yönetilen bir derlemeden diğerine geçirilen bir COM nesnesinin, alıcı derlemede uygun yönetilen türe yayınlanmasını anlamına gelir.

> [!NOTE]
> Tür denklik ve katıştırılmış birlikte çalışma türleri, uygulamalarla birlikte çalışma derlemeleri dağıtmak gerekli olmadığı için COM bileşenlerini kullanan uygulamaların ve eklentilerin dağıtımını basitleştirir. Paylaşılan COM bileşenlerinden oluşan geliştiricilerin, bileşenlerinin önceki .NET Framework sürümleri tarafından kullanılmasını istiyorsanız birincil birlikte çalışma derlemeleri (PIA 'lar) oluşturması gerekir.

## <a name="type-equivalence"></a>Tür denklik

 Arabirimler, yapılar, numaralandırmalar ve temsilciler için COM türlerinin denklik 'i desteklenir. Aşağıdaki koşulların tümü doğruysa COM türleri eşdeğer olarak niteler:

- Türler hem arabirimlerdir, hem de her iki yapı veya her ikisi de temsilcisdir.

- Türler, sonraki bölümde açıklandığı gibi aynı kimliğe sahiptir.

- Her iki tür de, tür denklik [IÇIN com türlerini işaretleme](#marking-com-types-for-type-equivalence) bölümünde açıklandığı gibi tür denklik için uygundur.

### <a name="type-identity"></a>Tür kimliği

İki tür, kapsamları ve kimlikleri eşleşiyorsa aynı kimliğe sahip olacak şekilde belirlenir, diğer bir deyişle, her birinin <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> özniteliği varsa ve iki özniteliğin eşleşen <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> ve <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> özellikleri vardır. İçin <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> karşılaştırma büyük/küçük harfe duyarlıdır.

Bir türün <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> özniteliği yoksa veya kapsam ve tanımlayıcı belirtmeyen bir <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> özniteliği varsa, tür şu şekilde denklik için de kabul edilebilir:

- Arabirimler <xref:System.Runtime.InteropServices.GuidAttribute> için, <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A?displayProperty=nameWithType> özelliği yerine öğesinin değeri kullanılır ve <xref:System.Type.FullName%2A?displayProperty=nameWithType> özelliği (diğer bir deyişle, ad alanı dahil olmak üzere tür adı), <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A?displayProperty=nameWithType> özelliği yerine kullanılır.

- <xref:System.Runtime.InteropServices.GuidAttribute> Yapılar, numaralandırmalar ve temsilciler için, kapsayan derlemenin <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> özelliği yerine kullanılır ve <xref:System.Type.FullName%2A?displayProperty=nameWithType> özelliği özelliği yerine <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> kullanılır.

### <a name="marking-com-types-for-type-equivalence"></a>Tür denklik için COM türleri işaretleniyor

 Tür denklik için uygun bir türü iki şekilde işaretleyebilirsiniz:

- <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> Özniteliği türüne uygulayın.

- Türü bir COM içeri aktarma türü yapın. Bir arabirim, <xref:System.Runtime.InteropServices.ComImportAttribute> ÖZNITELIĞI varsa com içeri aktarma türüdür. Arabirim, yapı, numaralandırma veya temsilci, tanımlanan derlemenin <xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute> ÖZNITELIĞI varsa com içeri aktarma türüdür.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Type.IsEquivalentTo%2A>
- [Yönetilen kodda COM türlerini kullanma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))
- [Tür Kitaplığını Derleme Olarak İçeri Aktarma](importing-a-type-library-as-an-assembly.md)
