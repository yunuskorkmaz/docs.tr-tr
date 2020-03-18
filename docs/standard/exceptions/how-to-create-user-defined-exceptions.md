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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708881"
---
# <a name="how-to-create-user-defined-exceptions"></a>Kullanıcı tanımlı özel durumlar nasıl oluşturulur?

.NET sonuçta taban sınıftan <xref:System.Exception>türetilen özel durum sınıfları bir hiyerarşi sağlar. Ancak, önceden tanımlanmış özel durumların hiçbiri gereksinimlerinizi karşılamazsa, <xref:System.Exception> sınıftan çıkararak kendi özel durum sınıflarınızı oluşturabilirsiniz.

Kendi özel durumlarınızı oluştururken, kullanıcı tarafından tanımlanan özel durum "Özel Durum" sözcüğüyle sonunuzu belirtin ve aşağıdaki örnekte gösterildiği gibi üç ortak oluşturucuyu uygulayın. Örnek adlı `EmployeeListNotFoundException`yeni bir özel durum sınıfı tanımlar. Sınıf türetilmiştir <xref:System.Exception> ve üç yapıcılar içerir.

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> Remoting kullandığınız durumlarda, kullanıcı tarafından tanımlanan özel durumlariçin meta verilerin sunucuda (callee) ve istemcide (proxy nesnesi veya arayan) kullanılabilir olduğundan emin olmalısınız. Daha fazla bilgi [için özel durumlar için en iyi uygulamalara](best-practices-for-exceptions.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Özel durumlar](index.md)
