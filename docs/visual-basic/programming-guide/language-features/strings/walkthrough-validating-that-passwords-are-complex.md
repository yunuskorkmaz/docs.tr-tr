---
title: "Doğrulama Parolalar karmaşıklık (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bdbe5f385c6b7a0898c4907b0d8afabdaed06fa0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a><span data-ttu-id="a6eca-102">İzlenecek yol: Parolaların Karmaşık Olduğunu Doğrulama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6eca-102">Walkthrough: Validating That Passwords Are Complex (Visual Basic)</span></span>
<span data-ttu-id="a6eca-103">Bu yöntem, bazı güçlü parola özelliklerini denetler ve bir dize parametresi hakkında Parola denetimlerini başarısız bilgilerle güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="a6eca-103">This method checks for some strong-password characteristics and updates a string parameter with information about which checks the password fails.</span></span>  
  
 <span data-ttu-id="a6eca-104">Parolaları güvenli bir sistemde bir kullanıcı yetki vermek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a6eca-104">Passwords can be used in a secure system to authorize a user.</span></span> <span data-ttu-id="a6eca-105">Ancak, parolalar yetkisiz kullanıcıların tahmin zor olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a6eca-105">However, the passwords must be difficult for unauthorized users to guess.</span></span> <span data-ttu-id="a6eca-106">Saldırganlar kullanabileceğiniz bir *sözlük saldırısı* tüm bir sözlük (veya birden çok sözlükler farklı dillerde) sözcükleri dolaşır ve herhangi bir sözcük bir kullanıcının parolasını çalışıp çalışmadığını test program.</span><span class="sxs-lookup"><span data-stu-id="a6eca-106">Attackers can use a *dictionary attack* program, which iterates through all of the words in a dictionary (or multiple dictionaries in different languages) and tests whether any of the words work as a user's password.</span></span> <span data-ttu-id="a6eca-107">"Yankees'i" veya "Mustang" gibi Zayıf parolalar kolayca tahmin edilebilir.</span><span class="sxs-lookup"><span data-stu-id="a6eca-107">Weak passwords such as "Yankees" or "Mustang" can be guessed quickly.</span></span> <span data-ttu-id="a6eca-108">Daha güçlü parolalar gibi "? 'L1N3vaFiNdMeyeP@sSWerd! ", Tahmin edilebilir daha az olasıdır.</span><span class="sxs-lookup"><span data-stu-id="a6eca-108">Stronger passwords, such as "?You'L1N3vaFiNdMeyeP@sSWerd!", are much less likely to be guessed.</span></span> <span data-ttu-id="a6eca-109">Parola korumalı bir sistem kullanıcıların güçlü parolalar seçtiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="a6eca-109">A password-protected system should ensure that users choose strong passwords.</span></span>  
  
 <span data-ttu-id="a6eca-110">Güçlü bir parola (büyük harf, küçük harfler, sayısal ve özel karakterler bir karışımını içeren) karmaşıktır ve bir sözcük değil.</span><span class="sxs-lookup"><span data-stu-id="a6eca-110">A strong password is complex (containing a mixture of uppercase, lowercase, numeric, and special characters) and is not a word.</span></span> <span data-ttu-id="a6eca-111">Bu örnek, karmaşıklık doğrulamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a6eca-111">This example demonstrates how to verify complexity.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6eca-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="a6eca-112">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="a6eca-113">Kod</span><span class="sxs-lookup"><span data-stu-id="a6eca-113">Code</span></span>  
 [!code-vb[VbVbcnRegEx#1](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/walkthrough-validating-that-passwords-are-complex_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a6eca-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="a6eca-114">Compiling the Code</span></span>  
 <span data-ttu-id="a6eca-115">Bu parolayı içeren dize geçirerek bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="a6eca-115">Call this method by passing the string that contains that password.</span></span>  
  
 <span data-ttu-id="a6eca-116">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="a6eca-116">This example requires:</span></span>  
  
-   <span data-ttu-id="a6eca-117">Üye erişimi <xref:System.Text.RegularExpressions> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="a6eca-117">Access to the members of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="a6eca-118">Ekleme bir `Imports` üye adlarının kodunuzda tam olarak niteleyemiyorsanız deyimi.</span><span class="sxs-lookup"><span data-stu-id="a6eca-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="a6eca-119">Daha fazla bilgi için bkz: [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="a6eca-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="a6eca-120">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="a6eca-120">Security</span></span>  
 <span data-ttu-id="a6eca-121">Bir ağ üzerinden parola taşıyorsanız, verileri aktarmak için güvenli bir yöntem kullanmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="a6eca-121">If you are moving the password across a network, you need to use a secure method for transferring data.</span></span> <span data-ttu-id="a6eca-122">Daha fazla bilgi için bkz: [ASP.NET Web uygulaması güvenliği](https://msdn.microsoft.com/library/330a99hc).</span><span class="sxs-lookup"><span data-stu-id="a6eca-122">For more information, see [ASP.NET Web Application Security](https://msdn.microsoft.com/library/330a99hc).</span></span>  
  
 <span data-ttu-id="a6eca-123">Doğruluğunu artırabilir `ValidatePassword` karmaşıklık denetimler ekleyerek işlevi:</span><span class="sxs-lookup"><span data-stu-id="a6eca-123">You can improve the accuracy of the `ValidatePassword` function by adding additional complexity checks:</span></span>  
  
-   <span data-ttu-id="a6eca-124">Parola ve onun alt dizeler kullanıcının adını, kullanıcı kimliği ve bir uygulama tanımlı sözlük karşı karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="a6eca-124">Compare the password and its substrings against the user's name, user identifier, and an application-defined dictionary.</span></span> <span data-ttu-id="a6eca-125">Ayrıca, görsel olarak benzer karakterler karşılaştırmaları gerçekleştirilirken eşdeğer olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="a6eca-125">In addition, treat visually similar characters as equivalent when performing the comparisons.</span></span> <span data-ttu-id="a6eca-126">Örneğin, harf "m" ve "e" eşdeğer rakamları "1" ve "3" olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="a6eca-126">For example, treat the letters "l" and "e" as equivalent to the numerals "1" and "3".</span></span>  
  
-   <span data-ttu-id="a6eca-127">Yalnızca bir büyük harf karakter ise, parolanın ilk karakter olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="a6eca-127">If there is only one uppercase character, make sure it is not the password's first character.</span></span>  
  
-   <span data-ttu-id="a6eca-128">Parolanın Son iki karakterler harf karakterler olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="a6eca-128">Make sure that the last two characters of the password are letter characters.</span></span>  
  
-   <span data-ttu-id="a6eca-129">Klavyenin ilk satırdaki tüm sembolleri girilen parolalar izin vermez.</span><span class="sxs-lookup"><span data-stu-id="a6eca-129">Do not allow passwords in which all the symbols are entered from the keyboard's top row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6eca-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a6eca-130">See Also</span></span>  
 <xref:System.Text.RegularExpressions.Regex>  
 [<span data-ttu-id="a6eca-131">ASP.NET Web uygulaması güvenliği</span><span class="sxs-lookup"><span data-stu-id="a6eca-131">ASP.NET Web Application Security</span></span>](https://msdn.microsoft.com/library/330a99hc)
