---
title: "Güvenlik ve Kullanıcı Girdisi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [.NET Framework], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 157e20a80f0a76e157fad091bec6bfe635a9ccb8
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="security-and-user-input"></a><span data-ttu-id="8d0f2-102">Güvenlik ve Kullanıcı Girdisi</span><span class="sxs-lookup"><span data-stu-id="8d0f2-102">Security and User Input</span></span>
<span data-ttu-id="8d0f2-103">Herhangi türde bir giriş (bir Web isteği veya URL, bir Microsoft Windows Forms uygulaması ve benzeri denetimleri için giriş verileri), genellikle bu verilere doğrudan parametre olarak başka bir kod çağırmak için kullanıldığından kod olumsuz yönde etkileyebilir kullanıcı verileri.</span><span class="sxs-lookup"><span data-stu-id="8d0f2-103">User data, which is any kind of input (data from a Web request or URL, input to controls of a Microsoft Windows Forms application, and so on), can adversely influence code because often that data is used directly as parameters to call other code.</span></span> <span data-ttu-id="8d0f2-104">Bu durum kötü amaçlı kod kodunuzu garip parametrelerle çağırma paraleldir ve aynı önlemler yapılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d0f2-104">This situation is analogous to malicious code calling your code with strange parameters, and the same precautions should be taken.</span></span> <span data-ttu-id="8d0f2-105">Kullanıcı girişi gerçekten zor olduğu için büyük olasılıkla güvenilmeyen veri izlemek için hiçbir yığın çerçevesi güvenli olmasını sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="8d0f2-105">User input is actually harder to make safe because there is no stack frame to trace the presence of the potentially untrusted data.</span></span>  
  
 <span data-ttu-id="8d0f2-106">Bunlar, bunlar için başka bir kod aracılığıyla hatalı veri iletmek için bir ağ geçidi, güvenlik görünen ilgisiz olan kod bulunabilir ancak çünkü bulmak için belirsiz ve en zor güvenlik hatalar arasındadır.</span><span class="sxs-lookup"><span data-stu-id="8d0f2-106">These are among the subtlest and hardest security bugs to find because, although they can exist in code that is seemingly unrelated to security, they are a gateway to pass bad data through to other code.</span></span> <span data-ttu-id="8d0f2-107">Bu hatalar için aramak için herhangi bir giriş verisi türünü izleyin, ne olası değerleri aralığı olabilir ve bu verileri görmesini kodu tüm durumlarda işlenip işlenmeyeceğini göz önünde bulundurun düşünün.</span><span class="sxs-lookup"><span data-stu-id="8d0f2-107">To look for these bugs, follow any kind of input data, imagine what the range of possible values might be, and consider whether the code seeing this data can handle all those cases.</span></span> <span data-ttu-id="8d0f2-108">Denetleme ve kod işleyemiyor herhangi bir giriş reddetme aralığı üzerinden bu hataları düzeltebilir.</span><span class="sxs-lookup"><span data-stu-id="8d0f2-108">You can fix these bugs through range checking and rejecting any input the code cannot handle.</span></span>  
  
 <span data-ttu-id="8d0f2-109">Kullanıcı verilerini içeren bazı önemli noktalar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8d0f2-109">Some important considerations involving user data include the following:</span></span>  
  
-   <span data-ttu-id="8d0f2-110">Sunucu yanıtı herhangi bir kullanıcı verisini istemcide sunucunun site bağlamında çalışır.</span><span class="sxs-lookup"><span data-stu-id="8d0f2-110">Any user data in a server response runs in the context of the server's site on the client.</span></span> <span data-ttu-id="8d0f2-111">Web sunucunuzun kullanıcı verileri alır ve döndürülen Web sayfasına ekler, örneğin, dahil bir  **\<komut dosyası >** etiketi ve sunucudan gibi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8d0f2-111">If your Web server takes user data and inserts it into the returned Web page, it might, for example, include a **\<script>** tag and run as if from the server.</span></span>  
  
-   <span data-ttu-id="8d0f2-112">İstemcinin herhangi bir URL isteyebileceği unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8d0f2-112">Remember that the client can request any URL.</span></span>  
  
-   <span data-ttu-id="8d0f2-113">Hassas ya da geçersiz yolları göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="8d0f2-113">Consider tricky or invalid paths:</span></span>  
  
    -   <span data-ttu-id="8d0f2-114">.. \, aşırı uzun yolları.</span><span class="sxs-lookup"><span data-stu-id="8d0f2-114">..\ , extremely long paths.</span></span>  
  
    -   <span data-ttu-id="8d0f2-115">Joker karakter (*) kullanın.</span><span class="sxs-lookup"><span data-stu-id="8d0f2-115">Use of wild card characters (*).</span></span>  
  
    -   <span data-ttu-id="8d0f2-116">Belirteç genişletme (% belirteci %).</span><span class="sxs-lookup"><span data-stu-id="8d0f2-116">Token expansion (%token%).</span></span>  
  
    -   <span data-ttu-id="8d0f2-117">Garip formları özel bir anlamı olan yol.</span><span class="sxs-lookup"><span data-stu-id="8d0f2-117">Strange forms of paths with special meaning.</span></span>  
  
    -   <span data-ttu-id="8d0f2-118">Dosya sistemi akışı adları gibi alternatif `filename::$DATA`.</span><span class="sxs-lookup"><span data-stu-id="8d0f2-118">Alternate file system stream names such as `filename::$DATA`.</span></span>  
  
    -   <span data-ttu-id="8d0f2-119">Dosya adlarının sürümleri gibi kısa `longfi~1` için `longfilename`.</span><span class="sxs-lookup"><span data-stu-id="8d0f2-119">Short versions of file names such as `longfi~1` for `longfilename`.</span></span>  
  
-   <span data-ttu-id="8d0f2-120">Eval(UserData) herhangi bir şey yapabileceğinizi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8d0f2-120">Remember that Eval(userdata) can do anything.</span></span>  
  
-   <span data-ttu-id="8d0f2-121">Bazı kullanıcı verilerini içeren bir ad olarak geç bağlama dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="8d0f2-121">Be wary of late binding to a name that includes some user data.</span></span>  
  
-   <span data-ttu-id="8d0f2-122">Web verilerle çalışıyorsanız dahil olmak üzere izin verilen, çıkışları çeşitli biçimlerde göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="8d0f2-122">If you are dealing with Web data, consider the various forms of escapes that are permissible, including:</span></span>  
  
    -   <span data-ttu-id="8d0f2-123">Onaltılık çıkışları (% nn).</span><span class="sxs-lookup"><span data-stu-id="8d0f2-123">Hexadecimal escapes (%nn).</span></span>  
  
    -   <span data-ttu-id="8d0f2-124">Unicode çıkışları (% nnn).</span><span class="sxs-lookup"><span data-stu-id="8d0f2-124">Unicode escapes (%nnn).</span></span>  
  
    -   <span data-ttu-id="8d0f2-125">Overlong UTF-8 çıkışları (% nn % nn).</span><span class="sxs-lookup"><span data-stu-id="8d0f2-125">Overlong UTF-8 escapes (%nn%nn).</span></span>  
  
    -   <span data-ttu-id="8d0f2-126">Çift kaçış karakterleri (% nn % mm '%' kaçış olduğu % mmnn olur).</span><span class="sxs-lookup"><span data-stu-id="8d0f2-126">Double escapes (%nn becomes %mmnn, where %mm is the escape for '%').</span></span>  
  
-   <span data-ttu-id="8d0f2-127">Birden fazla kurallı biçimi olabilecek kullanıcı adlarını dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="8d0f2-127">Be wary of user names that might have more than one canonical format.</span></span> <span data-ttu-id="8d0f2-128">Örneğin, genellikle ya da MYDOMAIN kullanabilirsiniz\\*kullanıcıadı* form veya *kullanıcıadı* @mydomain.example.com formu.</span><span class="sxs-lookup"><span data-stu-id="8d0f2-128">For example, you can often use either the MYDOMAIN\\*username* form or the *username*@mydomain.example.com form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d0f2-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8d0f2-129">See Also</span></span>  
 [<span data-ttu-id="8d0f2-130">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="8d0f2-130">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
