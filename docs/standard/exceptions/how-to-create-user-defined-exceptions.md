---
title: 'Nasıl yapılır: Kullanıcı Tanımlı Özel Durumlar Oluşturma'
description: .NET 'teki özel durum temel sınıfından türetilmiş özel durum sınıfları hiyerarşisine alternatif olan Kullanıcı tanımlı özel durumlar oluşturmayı öğrenin.
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
ms.openlocfilehash: 14eb6246ba4347f33766f7dff36463f2bf996330
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662803"
---
# <a name="how-to-create-user-defined-exceptions"></a><span data-ttu-id="71b03-103">Kullanıcı tanımlı özel durumlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="71b03-103">How to create user-defined exceptions</span></span>

<span data-ttu-id="71b03-104">.NET, sonunda temel sınıftan türetilmiş bir özel durum sınıfları hiyerarşisi sağlar <xref:System.Exception> .</span><span class="sxs-lookup"><span data-stu-id="71b03-104">.NET provides a hierarchy of exception classes ultimately derived from the base class <xref:System.Exception>.</span></span> <span data-ttu-id="71b03-105">Ancak, önceden tanımlı özel durumların hiçbiri gereksinimlerinizi karşılamıyorsa, sınıfından türeterek kendi özel durum sınıflarınızı oluşturabilirsiniz <xref:System.Exception> .</span><span class="sxs-lookup"><span data-stu-id="71b03-105">However, if none of the predefined exceptions meets your needs, you can create your own exception classes by deriving from the <xref:System.Exception> class.</span></span>

<span data-ttu-id="71b03-106">Kendi özel durumlarınızı oluştururken, Kullanıcı tanımlı özel durumun sınıf adını "özel durum" sözcüğüyle bitirin ve aşağıdaki örnekte gösterildiği gibi üç ortak Oluşturucu uygulayın.</span><span class="sxs-lookup"><span data-stu-id="71b03-106">When creating your own exceptions, end the class name of the user-defined exception with the word "Exception", and implement the three common constructors, as shown in the following example.</span></span> <span data-ttu-id="71b03-107">Örnek adlı yeni bir özel durum sınıfı tanımlar `EmployeeListNotFoundException` .</span><span class="sxs-lookup"><span data-stu-id="71b03-107">The example defines a new exception class named `EmployeeListNotFoundException`.</span></span> <span data-ttu-id="71b03-108">Sınıfı öğesinden türetilir <xref:System.Exception> ve üç Oluşturucu içerir.</span><span class="sxs-lookup"><span data-stu-id="71b03-108">The class is derived from <xref:System.Exception> and includes three constructors.</span></span>

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> <span data-ttu-id="71b03-109">Uzaktan iletişimi kullandığınız durumlarda, Kullanıcı tanımlı özel durumlar için meta verilerin sunucuda (aranan) ve istemcide (proxy nesne veya arayan) kullanılabilir olduğundan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="71b03-109">In situations where you are using remoting, you must ensure that the metadata for any user-defined exceptions is available at the server (callee) and to the client (the proxy object or caller).</span></span> <span data-ttu-id="71b03-110">Daha fazla bilgi için bkz. [özel durumlar Için en iyi uygulamalar](best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="71b03-110">For more information, see [Best practices for exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="71b03-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71b03-111">See also</span></span>

- [<span data-ttu-id="71b03-112">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="71b03-112">Exceptions</span></span>](index.md)
