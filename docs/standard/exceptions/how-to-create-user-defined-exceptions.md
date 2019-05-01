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
ms.openlocfilehash: dca313fad896ac1c8eac37c853657bea44a8b777
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970930"
---
# <a name="how-to-create-user-defined-exceptions"></a>Kullanıcı tanımlı özel durumlar oluşturma

.NET sağlar sonuçta taban sınıfından türetilen özel durum sınıfları hiyerarşisini <xref:System.Exception>. Önceden tanımlanmış özel durumlar hiçbiri gereksinimlerinizi karşılamıyorsa, Bununla birlikte, kendi özel durum sınıfları türeterek oluşturabileceğiniz <xref:System.Exception> sınıfı.

Kendi özel durumlar oluştururken, sınıf adı "Özel durum" sözcük kullanıcı tanımlı özel durumla sona ve aşağıdaki örnekte gösterildiği gibi üç ortak oluşturucu uygulayın. Örnek adlı yeni bir özel durum sınıfı tanımlar `EmployeeListNotFoundException`. Sınıf türetilir <xref:System.Exception> ve üç oluşturucular içerir.

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> Uzaktan iletişimini burada kullandığınız durumlarda, kullanıcı tanımlı özel durumlar için meta veriler (çağrılan) sunucusu ve istemcisi (proxy nesnesi veya çağıran) kullanılabilir olduğundan emin olun gerekir. Daha fazla bilgi için [özel durumlar için en iyi yöntemler](best-practices-for-exceptions.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durumlar](index.md)
