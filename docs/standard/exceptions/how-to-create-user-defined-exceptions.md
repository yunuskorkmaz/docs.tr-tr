---
title: 'Nasıl yapılır: Kullanıcı Tanımlı Özel Durumlar Oluşturma'
description: .NET 'teki özel durum temel sınıfından türetilmiş özel durum sınıfları hiyerarşisine alternatif olan Kullanıcı tanımlı özel durumlar oluşturmayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- user-defined exceptions
- exceptions, examples
- exceptions, user-defined
ms.assetid: 25819a5a-f915-4fc8-b924-a76915674e04
ms.openlocfilehash: b0a8549c9bacf322a0685c7b505185ab1d1101f6
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828133"
---
# <a name="how-to-create-user-defined-exceptions"></a>Kullanıcı tanımlı özel durumlar oluşturma

.NET, sonunda temel sınıftan türetilmiş bir özel durum sınıfları hiyerarşisi sağlar <xref:System.Exception> . Ancak, önceden tanımlı özel durumların hiçbiri gereksinimlerinizi karşılamıyorsa, sınıfından türeterek kendi özel durum sınıflarınızı oluşturabilirsiniz <xref:System.Exception> .

Kendi özel durumlarınızı oluştururken, Kullanıcı tanımlı özel durumun sınıf adını "özel durum" sözcüğüyle bitirin ve aşağıdaki örnekte gösterildiği gibi üç ortak Oluşturucu uygulayın. Örnek adlı yeni bir özel durum sınıfı tanımlar `EmployeeListNotFoundException` . Sınıfı öğesinden türetilir <xref:System.Exception> ve üç Oluşturucu içerir.

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> Uzaktan iletişimi kullandığınız durumlarda, Kullanıcı tanımlı özel durumlar için meta verilerin sunucuda (aranan) ve istemcide (proxy nesne veya arayan) kullanılabilir olduğundan emin olmanız gerekir. Daha fazla bilgi için bkz. [özel durumlar Için en iyi uygulamalar](best-practices-for-exceptions.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Özel durumlar](index.md)
