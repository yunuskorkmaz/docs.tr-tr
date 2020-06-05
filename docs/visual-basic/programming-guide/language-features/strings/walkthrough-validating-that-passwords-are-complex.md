---
title: Parola karmaşıklığı doğrulanıyor
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: 7b2d6a81f5dc88688a469b96d56a098a2b45c59f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363696"
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a><span data-ttu-id="483ed-102">İzlenecek yol: Parolaların Karmaşık Olduğunu Doğrulama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="483ed-102">Walkthrough: Validating That Passwords Are Complex (Visual Basic)</span></span>
<span data-ttu-id="483ed-103">Bu yöntem, bazı güçlü parola özelliklerini denetler ve parolanın başarısız olup olmadığını kontrol eden bilgilerle bir dize parametresini güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="483ed-103">This method checks for some strong-password characteristics and updates a string parameter with information about which checks the password fails.</span></span>  
  
 <span data-ttu-id="483ed-104">Parolalar, bir kullanıcıyı yetkilendirmek için güvenli bir sistemde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="483ed-104">Passwords can be used in a secure system to authorize a user.</span></span> <span data-ttu-id="483ed-105">Ancak, yetkisiz kullanıcıların tahmin edilmesi için parolaların kullanılması zor olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="483ed-105">However, the passwords must be difficult for unauthorized users to guess.</span></span> <span data-ttu-id="483ed-106">Saldırganlar bir Sözlükteki tüm sözcükleri (veya farklı dillerdeki birden çok sözlükleri) kullanarak bir *sözlük saldırı* programı kullanabilir ve sözcüklerin birinin Kullanıcı parolası olarak çalışıp çalışmadığını sınar.</span><span class="sxs-lookup"><span data-stu-id="483ed-106">Attackers can use a *dictionary attack* program, which iterates through all of the words in a dictionary (or multiple dictionaries in different languages) and tests whether any of the words work as a user's password.</span></span> <span data-ttu-id="483ed-107">"Yankees" veya "Mustang" gibi zayıf parolalar hızlı bir şekilde tahmin edilebilir.</span><span class="sxs-lookup"><span data-stu-id="483ed-107">Weak passwords such as "Yankees" or "Mustang" can be guessed quickly.</span></span> <span data-ttu-id="483ed-108">Daha güçlü parolalar (örneğin, "? ' L1N3vaFiNdMeyeP@sSWerd ! ", Tahmin edilebilir olma olasılığı çok daha az.</span><span class="sxs-lookup"><span data-stu-id="483ed-108">Stronger passwords, such as "?You'L1N3vaFiNdMeyeP@sSWerd!", are much less likely to be guessed.</span></span> <span data-ttu-id="483ed-109">Parola korumalı bir sistem, kullanıcıların güçlü parolalar seçmesini sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="483ed-109">A password-protected system should ensure that users choose strong passwords.</span></span>  
  
 <span data-ttu-id="483ed-110">Güçlü bir parola karmaşıktır (büyük harf, küçük harf, sayısal ve özel karakterlerin bir karışımını içeren) ve bir sözcük değildir.</span><span class="sxs-lookup"><span data-stu-id="483ed-110">A strong password is complex (containing a mixture of uppercase, lowercase, numeric, and special characters) and is not a word.</span></span> <span data-ttu-id="483ed-111">Bu örnek, karmaşıklığın nasıl doğrulanacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="483ed-111">This example demonstrates how to verify complexity.</span></span>  
  
## <a name="example"></a><span data-ttu-id="483ed-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="483ed-112">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="483ed-113">Kod</span><span class="sxs-lookup"><span data-stu-id="483ed-113">Code</span></span>  
 [!code-vb[VbVbcnRegEx#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#1)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="483ed-114">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="483ed-114">Compile the code</span></span>  
 <span data-ttu-id="483ed-115">Bu parolayı içeren dizeyi geçirerek bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="483ed-115">Call this method by passing the string that contains that password.</span></span>  
  
 <span data-ttu-id="483ed-116">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="483ed-116">This example requires:</span></span>  
  
- <span data-ttu-id="483ed-117"><xref:System.Text.RegularExpressions>Ad alanının üyelerine erişin.</span><span class="sxs-lookup"><span data-stu-id="483ed-117">Access to the members of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="483ed-118">`Imports`Kodunuzda üye adlarını tam olarak nitedıysanız bir ifade ekleyin.</span><span class="sxs-lookup"><span data-stu-id="483ed-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="483ed-119">Daha fazla bilgi için bkz. [Imports açıklaması (.net ad alanı ve türü)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="483ed-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="483ed-120">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="483ed-120">Security</span></span>  
 <span data-ttu-id="483ed-121">Parolayı bir ağ üzerinden taşıyorsanız, verileri aktarmak için güvenli bir yöntem kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="483ed-121">If you're moving the password across a network, you need to use a secure method for transferring data.</span></span> <span data-ttu-id="483ed-122">Daha fazla bilgi için bkz. [ASP.NET Web uygulaması güvenliği](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="483ed-122">For more information, see [ASP.NET Web Application Security](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100)).</span></span>
  
 <span data-ttu-id="483ed-123">`ValidatePassword`Ek karmaşıklık denetimleri ekleyerek işlevin doğruluğunu artırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="483ed-123">You can improve the accuracy of the `ValidatePassword` function by adding additional complexity checks:</span></span>  
  
- <span data-ttu-id="483ed-124">Parolayı ve alt dizelerini kullanıcının adı, Kullanıcı tanımlayıcısı ve uygulama tanımlı bir sözlükten karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="483ed-124">Compare the password and its substrings against the user's name, user identifier, and an application-defined dictionary.</span></span> <span data-ttu-id="483ed-125">Ayrıca, karşılaştırmaları gerçekleştirirken görsel açıdan benzer karakterleri eşdeğer olarak değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="483ed-125">In addition, treat visually similar characters as equivalent when performing the comparisons.</span></span> <span data-ttu-id="483ed-126">Örneğin, "l" ve "e" harflerini "1" ve "3" sayılarıyla eşdeğer olarak değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="483ed-126">For example, treat the letters "l" and "e" as equivalent to the numerals "1" and "3".</span></span>  
  
- <span data-ttu-id="483ed-127">Yalnızca bir büyük harf karakteri varsa, parolanın ilk karakteri olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="483ed-127">If there is only one uppercase character, make sure it is not the password's first character.</span></span>  
  
- <span data-ttu-id="483ed-128">Parolanın son iki karakterinin harf karakter olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="483ed-128">Make sure that the last two characters of the password are letter characters.</span></span>  
  
- <span data-ttu-id="483ed-129">Klavyenin en üst satırından tüm simgelerin girildiği parolalara izin vermeyin.</span><span class="sxs-lookup"><span data-stu-id="483ed-129">Do not allow passwords in which all the symbols are entered from the keyboard's top row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="483ed-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="483ed-130">See also</span></span>

- <xref:System.Text.RegularExpressions.Regex>
- <span data-ttu-id="483ed-131">[ASP.NET Web uygulaması güvenliği](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="483ed-131">[ASP.NET Web Application Security](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))</span></span>
