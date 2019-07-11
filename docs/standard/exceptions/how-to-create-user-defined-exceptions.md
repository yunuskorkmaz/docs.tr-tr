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
ms.openlocfilehash: 42860f549877436f43bfdc20fb3abde91d36101d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783185"
---
# <a name="how-to-create-user-defined-exceptions"></a><span data-ttu-id="93c26-102">Kullanıcı tanımlı özel durumlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="93c26-102">How to create user-defined exceptions</span></span>

<span data-ttu-id="93c26-103">.NET sağlar sonuçta taban sınıfından türetilen özel durum sınıfları hiyerarşisini <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="93c26-103">.NET provides a hierarchy of exception classes ultimately derived from the base class <xref:System.Exception>.</span></span> <span data-ttu-id="93c26-104">Önceden tanımlanmış özel durumlar hiçbiri gereksinimlerinizi karşılamıyorsa, Bununla birlikte, kendi özel durum sınıfları türeterek oluşturabileceğiniz <xref:System.Exception> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="93c26-104">However, if none of the predefined exceptions meets your needs, you can create your own exception classes by deriving from the <xref:System.Exception> class.</span></span>

<span data-ttu-id="93c26-105">Kendi özel durumlar oluştururken, sınıf adı "Özel durum" sözcük kullanıcı tanımlı özel durumla sona ve aşağıdaki örnekte gösterildiği gibi üç ortak oluşturucu uygulayın.</span><span class="sxs-lookup"><span data-stu-id="93c26-105">When creating your own exceptions, end the class name of the user-defined exception with the word "Exception", and implement the three common constructors, as shown in the following example.</span></span> <span data-ttu-id="93c26-106">Örnek adlı yeni bir özel durum sınıfı tanımlar `EmployeeListNotFoundException`.</span><span class="sxs-lookup"><span data-stu-id="93c26-106">The example defines a new exception class named `EmployeeListNotFoundException`.</span></span> <span data-ttu-id="93c26-107">Sınıf türetilir <xref:System.Exception> ve üç oluşturucular içerir.</span><span class="sxs-lookup"><span data-stu-id="93c26-107">The class is derived from <xref:System.Exception> and includes three constructors.</span></span>

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> <span data-ttu-id="93c26-108">Uzaktan iletişimini burada kullandığınız durumlarda, kullanıcı tanımlı özel durumlar için meta veriler (çağrılan) sunucusu ve istemcisi (proxy nesnesi veya çağıran) kullanılabilir olduğundan emin olun gerekir.</span><span class="sxs-lookup"><span data-stu-id="93c26-108">In situations where you are using remoting, you must ensure that the metadata for any user-defined exceptions is available at the server (callee) and to the client (the proxy object or caller).</span></span> <span data-ttu-id="93c26-109">Daha fazla bilgi için [özel durumlar için en iyi yöntemler](best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="93c26-109">For more information, see [Best practices for exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="93c26-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93c26-110">See also</span></span>

- [<span data-ttu-id="93c26-111">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="93c26-111">Exceptions</span></span>](index.md)
