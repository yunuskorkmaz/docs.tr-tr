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
# <a name="how-to-create-user-defined-exceptions"></a><span data-ttu-id="2995d-102">Kullanıcı tanımlı özel durumlar nasıl oluşturulur?</span><span class="sxs-lookup"><span data-stu-id="2995d-102">How to create user-defined exceptions</span></span>

<span data-ttu-id="2995d-103">.NET sonuçta taban sınıftan <xref:System.Exception>türetilen özel durum sınıfları bir hiyerarşi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2995d-103">.NET provides a hierarchy of exception classes ultimately derived from the base class <xref:System.Exception>.</span></span> <span data-ttu-id="2995d-104">Ancak, önceden tanımlanmış özel durumların hiçbiri gereksinimlerinizi karşılamazsa, <xref:System.Exception> sınıftan çıkararak kendi özel durum sınıflarınızı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2995d-104">However, if none of the predefined exceptions meets your needs, you can create your own exception classes by deriving from the <xref:System.Exception> class.</span></span>

<span data-ttu-id="2995d-105">Kendi özel durumlarınızı oluştururken, kullanıcı tarafından tanımlanan özel durum "Özel Durum" sözcüğüyle sonunuzu belirtin ve aşağıdaki örnekte gösterildiği gibi üç ortak oluşturucuyu uygulayın.</span><span class="sxs-lookup"><span data-stu-id="2995d-105">When creating your own exceptions, end the class name of the user-defined exception with the word "Exception", and implement the three common constructors, as shown in the following example.</span></span> <span data-ttu-id="2995d-106">Örnek adlı `EmployeeListNotFoundException`yeni bir özel durum sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2995d-106">The example defines a new exception class named `EmployeeListNotFoundException`.</span></span> <span data-ttu-id="2995d-107">Sınıf türetilmiştir <xref:System.Exception> ve üç yapıcılar içerir.</span><span class="sxs-lookup"><span data-stu-id="2995d-107">The class is derived from <xref:System.Exception> and includes three constructors.</span></span>

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> <span data-ttu-id="2995d-108">Remoting kullandığınız durumlarda, kullanıcı tarafından tanımlanan özel durumlariçin meta verilerin sunucuda (callee) ve istemcide (proxy nesnesi veya arayan) kullanılabilir olduğundan emin olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="2995d-108">In situations where you are using remoting, you must ensure that the metadata for any user-defined exceptions is available at the server (callee) and to the client (the proxy object or caller).</span></span> <span data-ttu-id="2995d-109">Daha fazla bilgi [için özel durumlar için en iyi uygulamalara](best-practices-for-exceptions.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="2995d-109">For more information, see [Best practices for exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2995d-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2995d-110">See also</span></span>

- [<span data-ttu-id="2995d-111">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="2995d-111">Exceptions</span></span>](index.md)
