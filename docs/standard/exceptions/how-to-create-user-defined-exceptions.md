---
title: "Nasıl yapılır: Kullanıcı Tanımlı Özel Durumlar Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- user-defined exceptions
- exceptions, examples
- exceptions, user-defined
ms.assetid: 25819a5a-f915-4fc8-b924-a76915674e04
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 68f2093e32fe2f9fbc0f826d2293a7b7f2e3c238
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/21/2017
---
# <a name="how-to-create-user-defined-exceptions"></a><span data-ttu-id="34254-102">Kullanıcı tanımlı özel durumlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="34254-102">How to create user-defined exceptions</span></span>

<span data-ttu-id="34254-103">.NET sağlar sonuçta temel sınıfından türetilen özel durum sınıfları hiyerarşisini <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="34254-103">.NET provides a hierarchy of exception classes ultimately derived from the base class <xref:System.Exception>.</span></span> <span data-ttu-id="34254-104">Önceden tanımlanmış özel durumlar hiçbiri gereksinimlerinizi karşılıyorsa, Bununla birlikte, kendi özel durum sınıfları türetme tarafından oluşturabileceğiniz <xref:System.Exception> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="34254-104">However, if none of the predefined exceptions meets your needs, you can create your own exception classes by deriving from the <xref:System.Exception> class.</span></span>

<span data-ttu-id="34254-105">Kendi özel durumlar oluştururken, kullanıcı tanımlı özel durum "Özel" sözcüğüyle sınıf adını sona ve aşağıdaki örnekte gösterildiği gibi üç ortak oluşturucuları uygulayın.</span><span class="sxs-lookup"><span data-stu-id="34254-105">When creating your own exceptions, end the class name of the user-defined exception with the word "Exception," and implement the three common constructors, as shown in the following example.</span></span> <span data-ttu-id="34254-106">Örnek adlı yeni bir özel durum sınıfı tanımlar `EmployeeListNotFoundException`.</span><span class="sxs-lookup"><span data-stu-id="34254-106">The example defines a new exception class named `EmployeeListNotFoundException`.</span></span> <span data-ttu-id="34254-107">Sınıfın türetildiği <xref:System.Exception> ve üç oluşturucular içerir.</span><span class="sxs-lookup"><span data-stu-id="34254-107">The class is derived from <xref:System.Exception> and includes three constructors.</span></span>

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> <span data-ttu-id="34254-108">Remoting kullandığınız durumlarda, kullanıcı tanımlı özel durumlar için meta veriler (aranan) sunucusu ve istemcisi (proxy nesnesi veya arayan) kullanılabilir olduğundan emin olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="34254-108">In situations where you are using remoting, you must ensure that the metadata for any user-defined exceptions is available at the server (callee) and to the client (the proxy object or caller).</span></span> <span data-ttu-id="34254-109">Daha fazla bilgi için bkz: [özel durumlar için en iyi uygulamaları](best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="34254-109">For more information, see [Best practices for exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="34254-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="34254-110">See Also</span></span>  
[<span data-ttu-id="34254-111">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="34254-111">Exceptions</span></span>](index.md)
