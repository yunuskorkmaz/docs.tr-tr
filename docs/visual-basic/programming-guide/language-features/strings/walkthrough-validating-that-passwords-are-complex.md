---
description: 'Daha fazla bilgi edinin: Izlenecek yol: parolaların karmaşık olduğunu doğrulama (Visual Basic)'
title: Parola karmaşıklığı doğrulanıyor
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: 608d9c7708058ca99196f2a06fd4ddd018aa0363
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471024"
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a><span data-ttu-id="a7e47-103">İzlenecek yol: Parolaların Karmaşık Olduğunu Doğrulama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7e47-103">Walkthrough: Validating That Passwords Are Complex (Visual Basic)</span></span>

<span data-ttu-id="a7e47-104">Bu yöntem, bazı güçlü parola özelliklerini denetler ve parolanın başarısız olup olmadığını kontrol eden bilgilerle bir dize parametresini güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="a7e47-104">This method checks for some strong-password characteristics and updates a string parameter with information about which checks the password fails.</span></span>  
  
 <span data-ttu-id="a7e47-105">Parolalar, bir kullanıcıyı yetkilendirmek için güvenli bir sistemde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a7e47-105">Passwords can be used in a secure system to authorize a user.</span></span> <span data-ttu-id="a7e47-106">Ancak, yetkisiz kullanıcıların tahmin edilmesi için parolaların kullanılması zor olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a7e47-106">However, the passwords must be difficult for unauthorized users to guess.</span></span> <span data-ttu-id="a7e47-107">Saldırganlar bir Sözlükteki tüm sözcükleri (veya farklı dillerdeki birden çok sözlükleri) kullanarak bir *sözlük saldırı* programı kullanabilir ve sözcüklerin birinin Kullanıcı parolası olarak çalışıp çalışmadığını sınar.</span><span class="sxs-lookup"><span data-stu-id="a7e47-107">Attackers can use a *dictionary attack* program, which iterates through all of the words in a dictionary (or multiple dictionaries in different languages) and tests whether any of the words work as a user's password.</span></span> <span data-ttu-id="a7e47-108">"Yankees" veya "Mustang" gibi zayıf parolalar hızlı bir şekilde tahmin edilebilir.</span><span class="sxs-lookup"><span data-stu-id="a7e47-108">Weak passwords such as "Yankees" or "Mustang" can be guessed quickly.</span></span> <span data-ttu-id="a7e47-109">Daha güçlü parolalar (örneğin, "? ' L1N3vaFiNdMeyeP@sSWerd ! ", Tahmin edilebilir olma olasılığı çok daha az.</span><span class="sxs-lookup"><span data-stu-id="a7e47-109">Stronger passwords, such as "?You'L1N3vaFiNdMeyeP@sSWerd!", are much less likely to be guessed.</span></span> <span data-ttu-id="a7e47-110">Parola korumalı bir sistem, kullanıcıların güçlü parolalar seçmesini sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a7e47-110">A password-protected system should ensure that users choose strong passwords.</span></span>  
  
 <span data-ttu-id="a7e47-111">Güçlü bir parola karmaşıktır (büyük harf, küçük harf, sayısal ve özel karakterlerin bir karışımını içeren) ve bir sözcük değildir.</span><span class="sxs-lookup"><span data-stu-id="a7e47-111">A strong password is complex (containing a mixture of uppercase, lowercase, numeric, and special characters) and is not a word.</span></span> <span data-ttu-id="a7e47-112">Bu örnek, karmaşıklığın nasıl doğrulanacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a7e47-112">This example demonstrates how to verify complexity.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7e47-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="a7e47-113">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="a7e47-114">Kod</span><span class="sxs-lookup"><span data-stu-id="a7e47-114">Code</span></span>  

 [!code-vb[VbVbcnRegEx#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#1)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="a7e47-115">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="a7e47-115">Compile the code</span></span>  

 <span data-ttu-id="a7e47-116">Bu parolayı içeren dizeyi geçirerek bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="a7e47-116">Call this method by passing the string that contains that password.</span></span>  
  
 <span data-ttu-id="a7e47-117">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="a7e47-117">This example requires:</span></span>  
  
- <span data-ttu-id="a7e47-118"><xref:System.Text.RegularExpressions>Ad alanının üyelerine erişin.</span><span class="sxs-lookup"><span data-stu-id="a7e47-118">Access to the members of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="a7e47-119">`Imports`Kodunuzda üye adlarını tam olarak nitedıysanız bir ifade ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a7e47-119">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="a7e47-120">Daha fazla bilgi için bkz. [Imports açıklaması (.net ad alanı ve türü)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="a7e47-120">For more information, see [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="a7e47-121">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="a7e47-121">Security</span></span>  

 <span data-ttu-id="a7e47-122">Parolayı bir ağ üzerinden taşıyorsanız, verileri aktarmak için güvenli bir yöntem kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a7e47-122">If you're moving the password across a network, you need to use a secure method for transferring data.</span></span> <span data-ttu-id="a7e47-123">Daha fazla bilgi için bkz. [ASP.NET Web uygulaması güvenliği](/previous-versions/aspnet/330a99hc(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a7e47-123">For more information, see [ASP.NET Web Application Security](/previous-versions/aspnet/330a99hc(v=vs.100)).</span></span>
  
 <span data-ttu-id="a7e47-124">`ValidatePassword`Ek karmaşıklık denetimleri ekleyerek işlevin doğruluğunu artırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a7e47-124">You can improve the accuracy of the `ValidatePassword` function by adding additional complexity checks:</span></span>  
  
- <span data-ttu-id="a7e47-125">Parolayı ve alt dizelerini kullanıcının adı, Kullanıcı tanımlayıcısı ve uygulama tanımlı bir sözlükten karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="a7e47-125">Compare the password and its substrings against the user's name, user identifier, and an application-defined dictionary.</span></span> <span data-ttu-id="a7e47-126">Ayrıca, karşılaştırmaları gerçekleştirirken görsel açıdan benzer karakterleri eşdeğer olarak değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="a7e47-126">In addition, treat visually similar characters as equivalent when performing the comparisons.</span></span> <span data-ttu-id="a7e47-127">Örneğin, "l" ve "e" harflerini "1" ve "3" sayılarıyla eşdeğer olarak değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="a7e47-127">For example, treat the letters "l" and "e" as equivalent to the numerals "1" and "3".</span></span>  
  
- <span data-ttu-id="a7e47-128">Yalnızca bir büyük harf karakteri varsa, parolanın ilk karakteri olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="a7e47-128">If there is only one uppercase character, make sure it is not the password's first character.</span></span>  
  
- <span data-ttu-id="a7e47-129">Parolanın son iki karakterinin harf karakter olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="a7e47-129">Make sure that the last two characters of the password are letter characters.</span></span>  
  
- <span data-ttu-id="a7e47-130">Klavyenin en üst satırından tüm simgelerin girildiği parolalara izin vermeyin.</span><span class="sxs-lookup"><span data-stu-id="a7e47-130">Do not allow passwords in which all the symbols are entered from the keyboard's top row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7e47-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7e47-131">See also</span></span>

- <xref:System.Text.RegularExpressions.Regex>
- <span data-ttu-id="a7e47-132">[ASP.NET Web uygulaması güvenliği](/previous-versions/aspnet/330a99hc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a7e47-132">[ASP.NET Web Application Security](/previous-versions/aspnet/330a99hc(v=vs.100))</span></span>
