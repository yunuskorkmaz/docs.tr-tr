---
title: 'Nasıl yapılır: Kullanıcı Tanımlı Özel Durumlar Oluşturma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- user-defined exceptions
- exceptions, examples
- exceptions, user-defined
ms.assetid: 25819a5a-f915-4fc8-b924-a76915674e04
ms.openlocfilehash: 6de00490a17fff005dd50a7acc5247089c073f68
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708881"
---
# <a name="how-to-create-user-defined-exceptions"></a>Kullanıcı tanımlı özel durumlar oluşturma

.NET, son olarak temel sınıftan türetilmiş bir özel durum sınıfları hiyerarşisi sağlar <xref:System.Exception>. Ancak, önceden tanımlı özel durumların hiçbiri gereksinimlerinizi karşılamıyorsa, <xref:System.Exception> sınıfından türeterek kendi özel durum sınıflarınızı oluşturabilirsiniz.

Kendi özel durumlarınızı oluştururken, Kullanıcı tanımlı özel durumun sınıf adını "özel durum" sözcüğüyle bitirin ve aşağıdaki örnekte gösterildiği gibi üç ortak Oluşturucu uygulayın. Örnek, `EmployeeListNotFoundException`adlı yeni bir özel durum sınıfı tanımlar. Sınıfı <xref:System.Exception> türetilir ve üç Oluşturucu içerir.

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> Uzaktan iletişimi kullandığınız durumlarda, Kullanıcı tanımlı özel durumlar için meta verilerin sunucuda (aranan) ve istemcide (proxy nesne veya arayan) kullanılabilir olduğundan emin olmanız gerekir. Daha fazla bilgi için bkz. [özel durumlar Için en iyi uygulamalar](best-practices-for-exceptions.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durumlar](index.md)
