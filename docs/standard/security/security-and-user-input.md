---
title: Güvenlik ve Kullanıcı Girdisi
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 27818d5e1779cd6e10e11830f91a20a3e638639a
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44127751"
---
# <a name="security-and-user-input"></a><span data-ttu-id="d371c-102">Güvenlik ve Kullanıcı Girdisi</span><span class="sxs-lookup"><span data-stu-id="d371c-102">Security and User Input</span></span>
<span data-ttu-id="d371c-103">Herhangi türde bir girdi (veriler bir Web isteği veya URL, bir Microsoft Windows Forms uygulaması ve benzeri denetimleri için giriş), bu verileri diğer kod çağırmak için doğrudan parametre olarak sıklıkla kullanılır çünkü kod olumsuz yönde etkileyebilir kullanıcı verileri.</span><span class="sxs-lookup"><span data-stu-id="d371c-103">User data, which is any kind of input (data from a Web request or URL, input to controls of a Microsoft Windows Forms application, and so on), can adversely influence code because often that data is used directly as parameters to call other code.</span></span> <span data-ttu-id="d371c-104">Bu durum kötü amaçlı kod kodunuzu garip parametrelerle çağırılıyor benzerdir ve aynı önlemler dikkat edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="d371c-104">This situation is analogous to malicious code calling your code with strange parameters, and the same precautions should be taken.</span></span> <span data-ttu-id="d371c-105">Kullanıcı Giriş potansiyel olarak güvenilmeyen veri izlemek için hiçbir yığın çerçevesi olduğundan güvenli hale getirmek için gerçekten daha zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="d371c-105">User input is actually harder to make safe because there is no stack frame to trace the presence of the potentially untrusted data.</span></span>  
  
 <span data-ttu-id="d371c-106">Bu, başka bir kod aracılığıyla hatalı veri iletmek için bir ağ geçidi olduğundan, güvenlik görünüşte ilgisiz olan kod bulunabilir ancak bunlar bulmak için belirsiz ve uygulamalarınızdaki güvenlik hatalar arasındadır.</span><span class="sxs-lookup"><span data-stu-id="d371c-106">These are among the subtlest and hardest security bugs to find because, although they can exist in code that is seemingly unrelated to security, they are a gateway to pass bad data through to other code.</span></span> <span data-ttu-id="d371c-107">Bu hatalar için aramak için giriş verileri herhangi bir türden izleyin, hangi olası değerleri aralığı olması ve bu verileri görme hakkındaki kod tüm durumlarda işlenip işlenmeyeceğini göz önünde bulundurun Imagine.</span><span class="sxs-lookup"><span data-stu-id="d371c-107">To look for these bugs, follow any kind of input data, imagine what the range of possible values might be, and consider whether the code seeing this data can handle all those cases.</span></span> <span data-ttu-id="d371c-108">Bu hatalar denetleme ve kodu işleyemiyor herhangi bir giriş reddetme aralığı düzeltebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d371c-108">You can fix these bugs through range checking and rejecting any input the code cannot handle.</span></span>  
  
 <span data-ttu-id="d371c-109">Kullanıcı verilerini içeren bazı önemli noktalar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d371c-109">Some important considerations involving user data include the following:</span></span>  
  
-   <span data-ttu-id="d371c-110">Tüm kullanıcı verilerini bir sunucu yanıtı sunucunun site bağlamında istemcide çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="d371c-110">Any user data in a server response runs in the context of the server's site on the client.</span></span> <span data-ttu-id="d371c-111">Web sunucunuzun kullanıcı verileri alır ve döndürülen Web sayfasına ekler, örneğin, içerebilir bir  **\<betik >** etiketleyin ve sunucudan gibi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d371c-111">If your Web server takes user data and inserts it into the returned Web page, it might, for example, include a **\<script>** tag and run as if from the server.</span></span>  
  
-   <span data-ttu-id="d371c-112">İstemcinin herhangi bir URL isteyebilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d371c-112">Remember that the client can request any URL.</span></span>  
  
-   <span data-ttu-id="d371c-113">Zor ya da geçersiz yolları göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="d371c-113">Consider tricky or invalid paths:</span></span>  
  
    -   <span data-ttu-id="d371c-114">.. \, son derece uzun yollar.</span><span class="sxs-lookup"><span data-stu-id="d371c-114">..\ , extremely long paths.</span></span>  
  
    -   <span data-ttu-id="d371c-115">Joker karakter (\*) kullanın.</span><span class="sxs-lookup"><span data-stu-id="d371c-115">Use of wild card characters (\*).</span></span>  
  
    -   <span data-ttu-id="d371c-116">Belirteç genişletme (% belirteci %).</span><span class="sxs-lookup"><span data-stu-id="d371c-116">Token expansion (%token%).</span></span>  
  
    -   <span data-ttu-id="d371c-117">Garip formları yolların özel anlama sahip.</span><span class="sxs-lookup"><span data-stu-id="d371c-117">Strange forms of paths with special meaning.</span></span>  
  
    -   <span data-ttu-id="d371c-118">Dosya sistemi akışı adları gibi alternatif `filename::$DATA`.</span><span class="sxs-lookup"><span data-stu-id="d371c-118">Alternate file system stream names such as `filename::$DATA`.</span></span>  
  
    -   <span data-ttu-id="d371c-119">Dosya adlarının sürümleri gibi kısa `longfi~1` için `longfilename`.</span><span class="sxs-lookup"><span data-stu-id="d371c-119">Short versions of file names such as `longfi~1` for `longfilename`.</span></span>  
  
-   <span data-ttu-id="d371c-120">Her şeyi yapabilirsiniz Eval(UserData) unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d371c-120">Remember that Eval(userdata) can do anything.</span></span>  
  
-   <span data-ttu-id="d371c-121">Bazı kullanıcı verilerini içeren bir ad, geç bağlama dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="d371c-121">Be wary of late binding to a name that includes some user data.</span></span>  
  
-   <span data-ttu-id="d371c-122">Web veri ile uğraşıyorsanız, çeşitli türleri dahil olmak üzere izin çıkar, göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="d371c-122">If you are dealing with Web data, consider the various forms of escapes that are permissible, including:</span></span>  
  
    -   <span data-ttu-id="d371c-123">Onaltılık kaçış karakterleri (% nn).</span><span class="sxs-lookup"><span data-stu-id="d371c-123">Hexadecimal escapes (%nn).</span></span>  
  
    -   <span data-ttu-id="d371c-124">Unicode kaçış karakterleri (% nnn).</span><span class="sxs-lookup"><span data-stu-id="d371c-124">Unicode escapes (%nnn).</span></span>  
  
    -   <span data-ttu-id="d371c-125">Overlong UTF-8 çıkar (% nn % nn).</span><span class="sxs-lookup"><span data-stu-id="d371c-125">Overlong UTF-8 escapes (%nn%nn).</span></span>  
  
    -   <span data-ttu-id="d371c-126">Çift kaçış karakterleri (% nn % mm '%' kaçış olduğu, % mmnn olur).</span><span class="sxs-lookup"><span data-stu-id="d371c-126">Double escapes (%nn becomes %mmnn, where %mm is the escape for '%').</span></span>  
  
-   <span data-ttu-id="d371c-127">Birden fazla kurallı biçimde olabilecek kullanıcı adlarını dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="d371c-127">Be wary of user names that might have more than one canonical format.</span></span> <span data-ttu-id="d371c-128">Örneğin, genellikle ya da MYDOMAIN kullanabilirsiniz\\*kullanıcıadı* form veya *kullanıcıadı* @mydomain.example.com form.</span><span class="sxs-lookup"><span data-stu-id="d371c-128">For example, you can often use either the MYDOMAIN\\*username* form or the *username*@mydomain.example.com form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d371c-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d371c-129">See also</span></span>

- [<span data-ttu-id="d371c-130">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="d371c-130">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
