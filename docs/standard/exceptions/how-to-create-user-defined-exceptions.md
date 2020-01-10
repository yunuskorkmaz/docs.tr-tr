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
# <a name="how-to-create-user-defined-exceptions"></a><span data-ttu-id="84246-102">Kullanıcı tanımlı özel durumlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="84246-102">How to create user-defined exceptions</span></span>

<span data-ttu-id="84246-103">.NET, son olarak temel sınıftan türetilmiş bir özel durum sınıfları hiyerarşisi sağlar <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="84246-103">.NET provides a hierarchy of exception classes ultimately derived from the base class <xref:System.Exception>.</span></span> <span data-ttu-id="84246-104">Ancak, önceden tanımlı özel durumların hiçbiri gereksinimlerinizi karşılamıyorsa, <xref:System.Exception> sınıfından türeterek kendi özel durum sınıflarınızı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84246-104">However, if none of the predefined exceptions meets your needs, you can create your own exception classes by deriving from the <xref:System.Exception> class.</span></span>

<span data-ttu-id="84246-105">Kendi özel durumlarınızı oluştururken, Kullanıcı tanımlı özel durumun sınıf adını "özel durum" sözcüğüyle bitirin ve aşağıdaki örnekte gösterildiği gibi üç ortak Oluşturucu uygulayın.</span><span class="sxs-lookup"><span data-stu-id="84246-105">When creating your own exceptions, end the class name of the user-defined exception with the word "Exception", and implement the three common constructors, as shown in the following example.</span></span> <span data-ttu-id="84246-106">Örnek, `EmployeeListNotFoundException`adlı yeni bir özel durum sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="84246-106">The example defines a new exception class named `EmployeeListNotFoundException`.</span></span> <span data-ttu-id="84246-107">Sınıfı <xref:System.Exception> türetilir ve üç Oluşturucu içerir.</span><span class="sxs-lookup"><span data-stu-id="84246-107">The class is derived from <xref:System.Exception> and includes three constructors.</span></span>

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> <span data-ttu-id="84246-108">Uzaktan iletişimi kullandığınız durumlarda, Kullanıcı tanımlı özel durumlar için meta verilerin sunucuda (aranan) ve istemcide (proxy nesne veya arayan) kullanılabilir olduğundan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="84246-108">In situations where you are using remoting, you must ensure that the metadata for any user-defined exceptions is available at the server (callee) and to the client (the proxy object or caller).</span></span> <span data-ttu-id="84246-109">Daha fazla bilgi için bkz. [özel durumlar Için en iyi uygulamalar](best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="84246-109">For more information, see [Best practices for exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="84246-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84246-110">See also</span></span>

- [<span data-ttu-id="84246-111">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="84246-111">Exceptions</span></span>](index.md)
