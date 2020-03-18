---
title: Güvenlik ve Kullanıcı Girdisi
description: Kodunuz, kullanıcı tarafından girilen verileri, güvenliği etkileyebilecek diğer kodlara parametre olarak geçirebilir. Sorunlu girişi reddetmek için aralık denetimi yapabilirsiniz.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
ms.openlocfilehash: fa9f8d4708e928c51e446d8369c9b4556fc6fb77
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186101"
---
# <a name="security-and-user-input"></a><span data-ttu-id="152ce-104">Güvenlik ve Kullanıcı Girdisi</span><span class="sxs-lookup"><span data-stu-id="152ce-104">Security and User Input</span></span>

<span data-ttu-id="152ce-105">Her türlü girdi (Web isteği veya URL'den alınan veriler, Microsoft Windows Forms uygulamasının denetimlerine giriş vb.) kullanıcı verileri, genellikle bu veriler diğer kodları aramak için doğrudan parametre olarak kullanıldığından kodu olumsuz etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="152ce-105">User data, which is any kind of input (data from a Web request or URL, input to controls of a Microsoft Windows Forms application, and so on), can adversely influence code because often that data is used directly as parameters to call other code.</span></span> <span data-ttu-id="152ce-106">Bu durum, kodunuzu garip parametrelerle çağıran kötü amaçlı koda benzer ve aynı önlemler alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="152ce-106">This situation is analogous to malicious code calling your code with strange parameters, and the same precautions should be taken.</span></span> <span data-ttu-id="152ce-107">Kullanıcı girişinin güvenli olması aslında zordur, çünkü güvenilmeyen verilerin varlığını izlemek için yığın çerçevesi yoktur.</span><span class="sxs-lookup"><span data-stu-id="152ce-107">User input is actually harder to make safe because there is no stack frame to trace the presence of the potentially untrusted data.</span></span>

<span data-ttu-id="152ce-108">Bunlar, güvenlikle ilgisi olmayan bir kodda bulunabilseler de, kötü verileri diğer kodlara aktarmak için bir ağ geçidi olduğundan, bulunması en ince ve en zor güvenlik hataları arasındadır.</span><span class="sxs-lookup"><span data-stu-id="152ce-108">These are among the subtlest and hardest security bugs to find because, although they can exist in code that is seemingly unrelated to security, they are a gateway to pass bad data through to other code.</span></span> <span data-ttu-id="152ce-109">Bu hataları aramak için, her türlü giriş verilerini izleyin, olası değerlerin aralığının ne olabileceğini hayal edin ve bu verileri gören kodun tüm bu servis taleplerini işleyip işlemeyebileceğini düşünün.</span><span class="sxs-lookup"><span data-stu-id="152ce-109">To look for these bugs, follow any kind of input data, imagine what the range of possible values might be, and consider whether the code seeing this data can handle all those cases.</span></span> <span data-ttu-id="152ce-110">Bu hataları, kodun işleyemeyeceği herhangi bir girişi aralık denetimi ve reddederek düzeltebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="152ce-110">You can fix these bugs through range checking and rejecting any input the code cannot handle.</span></span>

<span data-ttu-id="152ce-111">Kullanıcı verilerini içeren bazı önemli hususlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="152ce-111">Some important considerations involving user data include the following:</span></span>

- <span data-ttu-id="152ce-112">Sunucu yanıtındaki tüm kullanıcı verileri istemcide sunucunun sitesi bağlamında çalışır.</span><span class="sxs-lookup"><span data-stu-id="152ce-112">Any user data in a server response runs in the context of the server's site on the client.</span></span> <span data-ttu-id="152ce-113">Web sunucunuz kullanıcı verilerini alıp döndürülen Web sayfasına eklerse, örneğin \*\* \<\*\* bir komut dosyası>etiketi ekleyebilir ve sunucudan geliyormuş gibi çalıştırAbilir.</span><span class="sxs-lookup"><span data-stu-id="152ce-113">If your Web server takes user data and inserts it into the returned Web page, it might, for example, include a **\<script>** tag and run as if from the server.</span></span>

- <span data-ttu-id="152ce-114">İstemcinin herhangi bir URL isteyebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="152ce-114">Remember that the client can request any URL.</span></span>

- <span data-ttu-id="152ce-115">Zor veya geçersiz yolları göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="152ce-115">Consider tricky or invalid paths:</span></span>

  - <span data-ttu-id="152ce-116">.. \ , son derece uzun yollar.</span><span class="sxs-lookup"><span data-stu-id="152ce-116">..\ , extremely long paths.</span></span>

  - <span data-ttu-id="152ce-117">Joker karakter kullanımı (\*).</span><span class="sxs-lookup"><span data-stu-id="152ce-117">Use of wild card characters (\*).</span></span>

  - <span data-ttu-id="152ce-118">Belirteç genişlemesi (%token%).</span><span class="sxs-lookup"><span data-stu-id="152ce-118">Token expansion (%token%).</span></span>

  - <span data-ttu-id="152ce-119">Özel anlamı olan yolların garip formları.</span><span class="sxs-lookup"><span data-stu-id="152ce-119">Strange forms of paths with special meaning.</span></span>

  - <span data-ttu-id="152ce-120">Alternatif dosya sistemi akışı `filename::$DATA`adları gibi .</span><span class="sxs-lookup"><span data-stu-id="152ce-120">Alternate file system stream names such as `filename::$DATA`.</span></span>

  - <span data-ttu-id="152ce-121">için `longfi~1` `longfilename`gibi dosya adlarının kısa sürümleri.</span><span class="sxs-lookup"><span data-stu-id="152ce-121">Short versions of file names such as `longfi~1` for `longfilename`.</span></span>

- <span data-ttu-id="152ce-122">Eval'in (userdata) her şeyi yapabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="152ce-122">Remember that Eval(userdata) can do anything.</span></span>

- <span data-ttu-id="152ce-123">Bazı kullanıcı verilerini içeren bir ada geç bağlanmakonusunda dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="152ce-123">Be wary of late binding to a name that includes some user data.</span></span>

- <span data-ttu-id="152ce-124">Web verileriyle ilgileniyorsanız, aşağıdakiler de dahil olmak üzere izin verilen çeşitli kaçış biçimlerini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="152ce-124">If you are dealing with Web data, consider the various forms of escapes that are permissible, including:</span></span>

  - <span data-ttu-id="152ce-125">Hexadecimal kaçışlar (%nn).</span><span class="sxs-lookup"><span data-stu-id="152ce-125">Hexadecimal escapes (%nn).</span></span>

  - <span data-ttu-id="152ce-126">Unicode kaçar (%nnn).</span><span class="sxs-lookup"><span data-stu-id="152ce-126">Unicode escapes (%nnn).</span></span>

  - <span data-ttu-id="152ce-127">Overlong UTF-8 kaçar (%nn%nn).</span><span class="sxs-lookup"><span data-stu-id="152ce-127">Overlong UTF-8 escapes (%nn%nn).</span></span>

  - <span data-ttu-id="152ce-128">Çift kaçış (%nn %mmnn olur, %mm '%') için kaçış olur.</span><span class="sxs-lookup"><span data-stu-id="152ce-128">Double escapes (%nn becomes %mmnn, where %mm is the escape for '%').</span></span>

- <span data-ttu-id="152ce-129">Birden fazla kanonik biçimi olabilecek kullanıcı adlarıyla dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="152ce-129">Be wary of user names that might have more than one canonical format.</span></span> <span data-ttu-id="152ce-130">Örneğin,\\mydomain*kullanıcı adı* formunu veya kullanıcı *adı* @mydomain.example.com formunu sık sık kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="152ce-130">For example, you can often use either the MYDOMAIN\\*username* form or the *username*@mydomain.example.com form.</span></span>

## <a name="see-also"></a><span data-ttu-id="152ce-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="152ce-131">See also</span></span>

- [<span data-ttu-id="152ce-132">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="152ce-132">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
