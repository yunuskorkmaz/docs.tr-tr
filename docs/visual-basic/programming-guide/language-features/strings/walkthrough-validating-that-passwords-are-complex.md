---
title: Parolalar karmaşıklık (Visual Basic) doğrulanıyor
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: 829d6485acdca22fbf10160c734e5c7f931dd855
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824942"
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a><span data-ttu-id="68efe-102">İzlenecek yol: Parolaların karmaşık olduğunu doğrulama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68efe-102">Walkthrough: Validating That Passwords Are Complex (Visual Basic)</span></span>
<span data-ttu-id="68efe-103">Bu yöntem, bazı güçlü parola özelliklerini denetler ve bir dize parametresi başarısız parola denetleyen hakkında bilgilerle güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="68efe-103">This method checks for some strong-password characteristics and updates a string parameter with information about which checks the password fails.</span></span>  
  
 <span data-ttu-id="68efe-104">Parolalar güvenli bir sistemde bir kullanıcıyı yetkilendirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="68efe-104">Passwords can be used in a secure system to authorize a user.</span></span> <span data-ttu-id="68efe-105">Ancak, parola yetkisiz kullanıcıların tahmin zor olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="68efe-105">However, the passwords must be difficult for unauthorized users to guess.</span></span> <span data-ttu-id="68efe-106">Saldırganlar kullanabileceğiniz bir *sözlük saldırıları* tüm bir sözlük (veya birden çok sözlükleri farklı dillerde) bir kelimelerin gezinir ve herhangi bir kelimelerin bir kullanıcının parolasını çalışıp çalışmadığını test programı.</span><span class="sxs-lookup"><span data-stu-id="68efe-106">Attackers can use a *dictionary attack* program, which iterates through all of the words in a dictionary (or multiple dictionaries in different languages) and tests whether any of the words work as a user's password.</span></span> <span data-ttu-id="68efe-107">Zayıf parolalarda "Yankees'in" veya "Mustang" gibi hızlı bir şekilde tahmin edilebilir.</span><span class="sxs-lookup"><span data-stu-id="68efe-107">Weak passwords such as "Yankees" or "Mustang" can be guessed quickly.</span></span> <span data-ttu-id="68efe-108">Güçlü parolalar gibi "? 'L1N3vaFiNdMeyeP@sSWerd! ", Tahmin edilebilir çok daha düşüktür.</span><span class="sxs-lookup"><span data-stu-id="68efe-108">Stronger passwords, such as "?You'L1N3vaFiNdMeyeP@sSWerd!", are much less likely to be guessed.</span></span> <span data-ttu-id="68efe-109">Parola korumalı bir sistem kullanıcıların güçlü parolalar seçtiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="68efe-109">A password-protected system should ensure that users choose strong passwords.</span></span>  
  
 <span data-ttu-id="68efe-110">Güçlü bir parola (büyük harf, küçük harfler, sayısal ve özel karakterler bir karışımını içeren) karmaşıktır ve bir sözcük değildir.</span><span class="sxs-lookup"><span data-stu-id="68efe-110">A strong password is complex (containing a mixture of uppercase, lowercase, numeric, and special characters) and is not a word.</span></span> <span data-ttu-id="68efe-111">Bu örnek, karmaşıklık doğrulamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="68efe-111">This example demonstrates how to verify complexity.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68efe-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="68efe-112">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="68efe-113">Kod</span><span class="sxs-lookup"><span data-stu-id="68efe-113">Code</span></span>  
 [!code-vb[VbVbcnRegEx#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="68efe-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="68efe-114">Compiling the Code</span></span>  
 <span data-ttu-id="68efe-115">Bu parolayı içeren dizeyi geçirerek bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="68efe-115">Call this method by passing the string that contains that password.</span></span>  
  
 <span data-ttu-id="68efe-116">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="68efe-116">This example requires:</span></span>  
  
-   <span data-ttu-id="68efe-117">Üye erişimi <xref:System.Text.RegularExpressions> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="68efe-117">Access to the members of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="68efe-118">Ekleme bir `Imports` üye adları kodunuzda tamamen niteleyemiyorsanız deyimi.</span><span class="sxs-lookup"><span data-stu-id="68efe-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="68efe-119">Daha fazla bilgi için [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="68efe-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="68efe-120">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="68efe-120">Security</span></span>  
 <span data-ttu-id="68efe-121">Parola ağ üzerinden taşıyorsanız, verileri aktarmak için güvenli bir yöntem kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="68efe-121">If you're moving the password across a network, you need to use a secure method for transferring data.</span></span> <span data-ttu-id="68efe-122">Daha fazla bilgi için [ASP.NET Web uygulaması güvenliği](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="68efe-122">For more information, see [ASP.NET Web Application Security](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100)).</span></span>
  
 <span data-ttu-id="68efe-123">Doğruluğunu geliştirebilir `ValidatePassword` karmaşıklık denetimleri ekleyerek işlevi:</span><span class="sxs-lookup"><span data-stu-id="68efe-123">You can improve the accuracy of the `ValidatePassword` function by adding additional complexity checks:</span></span>  
  
-   <span data-ttu-id="68efe-124">Parola ve onun alt dizeler kullanıcının adını, kullanıcı kimliği ve uygulama tanımlı bir sözlük karşı karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="68efe-124">Compare the password and its substrings against the user's name, user identifier, and an application-defined dictionary.</span></span> <span data-ttu-id="68efe-125">Ayrıca, görsel olarak benzer karakterler karşılaştırmaları yaparken eşdeğer olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="68efe-125">In addition, treat visually similar characters as equivalent when performing the comparisons.</span></span> <span data-ttu-id="68efe-126">Örneğin, "e" ve "m" harf "1" ve "3" simgeleridir eşdeğer olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="68efe-126">For example, treat the letters "l" and "e" as equivalent to the numerals "1" and "3".</span></span>  
  
-   <span data-ttu-id="68efe-127">Yalnızca bir büyük harf karakter varsa, parolanın ilk karakteri olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="68efe-127">If there is only one uppercase character, make sure it is not the password's first character.</span></span>  
  
-   <span data-ttu-id="68efe-128">Parola en son iki karakter harf karakterler olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="68efe-128">Make sure that the last two characters of the password are letter characters.</span></span>  
  
-   <span data-ttu-id="68efe-129">Klavyenin üst satırdaki tüm sembolleri girilen parolaları izin vermez.</span><span class="sxs-lookup"><span data-stu-id="68efe-129">Do not allow passwords in which all the symbols are entered from the keyboard's top row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68efe-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68efe-130">See also</span></span>

- <xref:System.Text.RegularExpressions.Regex>
- <span data-ttu-id="68efe-131">[ASP.NET Web uygulaması güvenliği](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="68efe-131">[ASP.NET Web Application Security](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))</span></span>
