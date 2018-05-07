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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 90bf9d6dbfebf8f7c1aa22e5844cf4e30b89b8d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-user-defined-exceptions"></a>Kullanıcı tanımlı özel durumlar oluşturma

.NET sağlar sonuçta temel sınıfından türetilen özel durum sınıfları hiyerarşisini <xref:System.Exception>. Önceden tanımlanmış özel durumlar hiçbiri gereksinimlerinizi karşılıyorsa, Bununla birlikte, kendi özel durum sınıfları türetme tarafından oluşturabileceğiniz <xref:System.Exception> sınıfı.

Kendi özel durumlar oluştururken, kullanıcı tanımlı özel durum "Özel" sözcüğüyle sınıf adını sona ve aşağıdaki örnekte gösterildiği gibi üç ortak oluşturucuları uygulayın. Örnek adlı yeni bir özel durum sınıfı tanımlar `EmployeeListNotFoundException`. Sınıfın türetildiği <xref:System.Exception> ve üç oluşturucular içerir.

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> Remoting kullandığınız durumlarda, kullanıcı tanımlı özel durumlar için meta veriler (aranan) sunucusu ve istemcisi (proxy nesnesi veya arayan) kullanılabilir olduğundan emin olmalısınız. Daha fazla bilgi için bkz: [özel durumlar için en iyi uygulamaları](best-practices-for-exceptions.md).

## <a name="see-also"></a>Ayrıca Bkz.  
[Özel Durumlar](index.md)
