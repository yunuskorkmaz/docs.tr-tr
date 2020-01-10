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
ms.openlocfilehash: 0d34b06b44241feb7d6e3c8f76447b861563cfdc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705866"
---
# <a name="security-and-user-input"></a><span data-ttu-id="827a6-102">Güvenlik ve Kullanıcı Girdisi</span><span class="sxs-lookup"><span data-stu-id="827a6-102">Security and User Input</span></span>

<span data-ttu-id="827a6-103">Her türlü giriş (bir Web isteği veya URL 'deki veriler, bir Microsoft Windows Forms uygulamasının denetimlerine giriş vb.) olan Kullanıcı verileri, genellikle bu veriler diğer kodu çağırmak için parametre olarak doğrudan kullanıldığı için kodu olumsuz etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="827a6-103">User data, which is any kind of input (data from a Web request or URL, input to controls of a Microsoft Windows Forms application, and so on), can adversely influence code because often that data is used directly as parameters to call other code.</span></span> <span data-ttu-id="827a6-104">Bu durum, kodunuzu garip parametrelerle çağıran kötü amaçlı koda benzer ve aynı önlemler alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="827a6-104">This situation is analogous to malicious code calling your code with strange parameters, and the same precautions should be taken.</span></span> <span data-ttu-id="827a6-105">Potansiyel olarak güvenilmeyen verilerin varlığını izlemek için yığın çerçevesi bulunmadığından, Kullanıcı girişi gerçekten güvenli hale getirmek daha zordur.</span><span class="sxs-lookup"><span data-stu-id="827a6-105">User input is actually harder to make safe because there is no stack frame to trace the presence of the potentially untrusted data.</span></span>

<span data-ttu-id="827a6-106">Bunlar, güvenlikle ilgili olmayan bir kodda bulunabilseler de, güvenlikle ilgili olan ve diğer koda yönelik hatalı verileri geçirmeye yönelik bir ağ geçidinizin olan alt en uzun ve en yüksek güvenlik hatalarının arasındadır.</span><span class="sxs-lookup"><span data-stu-id="827a6-106">These are among the subtlest and hardest security bugs to find because, although they can exist in code that is seemingly unrelated to security, they are a gateway to pass bad data through to other code.</span></span> <span data-ttu-id="827a6-107">Bu hataları aramak için, her türlü giriş verilerini izleyin, olası değerlerin aralığının ne olabileceğini düşünün ve bu verileri gördüğü kodun tüm bu durumları işleyebileceğini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="827a6-107">To look for these bugs, follow any kind of input data, imagine what the range of possible values might be, and consider whether the code seeing this data can handle all those cases.</span></span> <span data-ttu-id="827a6-108">Bu hataları Aralık denetleme ve kodun işleyemeyeceği herhangi bir girişi reddetme yoluyla çözebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="827a6-108">You can fix these bugs through range checking and rejecting any input the code cannot handle.</span></span>

<span data-ttu-id="827a6-109">Kullanıcı verileriyle ilgili bazı önemli noktalar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="827a6-109">Some important considerations involving user data include the following:</span></span>

- <span data-ttu-id="827a6-110">Sunucu yanıtındaki herhangi bir kullanıcı verisi, istemci üzerindeki sunucunun sitesi bağlamında çalışır.</span><span class="sxs-lookup"><span data-stu-id="827a6-110">Any user data in a server response runs in the context of the server's site on the client.</span></span> <span data-ttu-id="827a6-111">Web sunucunuz kullanıcı verilerini alıp döndürülen Web sayfasına eklediğinde, örneğin, bir **\<betik >** etiketi içerebilir ve sunucuda olduğu gibi çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="827a6-111">If your Web server takes user data and inserts it into the returned Web page, it might, for example, include a **\<script>** tag and run as if from the server.</span></span>

- <span data-ttu-id="827a6-112">İstemcinin herhangi bir URL isteyeolabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="827a6-112">Remember that the client can request any URL.</span></span>

- <span data-ttu-id="827a6-113">Karmaşık veya geçersiz yolları göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="827a6-113">Consider tricky or invalid paths:</span></span>

  - <span data-ttu-id="827a6-114">.. \, son derece uzun yollar.</span><span class="sxs-lookup"><span data-stu-id="827a6-114">..\ , extremely long paths.</span></span>

  - <span data-ttu-id="827a6-115">Joker karakter (\*) kullanın.</span><span class="sxs-lookup"><span data-stu-id="827a6-115">Use of wild card characters (\*).</span></span>

  - <span data-ttu-id="827a6-116">Belirteç genişletmesi (% token%).</span><span class="sxs-lookup"><span data-stu-id="827a6-116">Token expansion (%token%).</span></span>

  - <span data-ttu-id="827a6-117">Özel anlamlara sahip garip yol biçimleri.</span><span class="sxs-lookup"><span data-stu-id="827a6-117">Strange forms of paths with special meaning.</span></span>

  - <span data-ttu-id="827a6-118">`filename::$DATA`gibi alternatif dosya sistemi akış adları.</span><span class="sxs-lookup"><span data-stu-id="827a6-118">Alternate file system stream names such as `filename::$DATA`.</span></span>

  - <span data-ttu-id="827a6-119">`longfilename`için `longfi~1` gibi dosya adlarının kısa sürümleri.</span><span class="sxs-lookup"><span data-stu-id="827a6-119">Short versions of file names such as `longfi~1` for `longfilename`.</span></span>

- <span data-ttu-id="827a6-120">Eval (UserData) her şeyi yapabildiği unutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="827a6-120">Remember that Eval(userdata) can do anything.</span></span>

- <span data-ttu-id="827a6-121">Bazı Kullanıcı verilerini içeren bir ada geç bağlama konusunda dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="827a6-121">Be wary of late binding to a name that includes some user data.</span></span>

- <span data-ttu-id="827a6-122">Web verileriyle uğraşıyorsanız, aşağıdakiler de dahil olmak üzere, izin verilen çeşitli kaçış biçimlerini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="827a6-122">If you are dealing with Web data, consider the various forms of escapes that are permissible, including:</span></span>

  - <span data-ttu-id="827a6-123">Onaltılı kaçış (% nn).</span><span class="sxs-lookup"><span data-stu-id="827a6-123">Hexadecimal escapes (%nn).</span></span>

  - <span data-ttu-id="827a6-124">Unicode kaçış (% nnn).</span><span class="sxs-lookup"><span data-stu-id="827a6-124">Unicode escapes (%nnn).</span></span>

  - <span data-ttu-id="827a6-125">Fazla uzun UTF-8 kaçış (% nn% nn).</span><span class="sxs-lookup"><span data-stu-id="827a6-125">Overlong UTF-8 escapes (%nn%nn).</span></span>

  - <span data-ttu-id="827a6-126">Çift kaçış (% nn,% mm '% ' için kaçış olduğu için% mmnn olur).</span><span class="sxs-lookup"><span data-stu-id="827a6-126">Double escapes (%nn becomes %mmnn, where %mm is the escape for '%').</span></span>

- <span data-ttu-id="827a6-127">Birden fazla kurallı biçimi olabilecek kullanıcı adlarına karşı dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="827a6-127">Be wary of user names that might have more than one canonical format.</span></span> <span data-ttu-id="827a6-128">Örneğin, çoğunlukla ETKIALANıM\\*Kullanıcı adı* formunu veya *Kullanıcı adı*@mydomain.example.com formunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="827a6-128">For example, you can often use either the MYDOMAIN\\*username* form or the *username*@mydomain.example.com form.</span></span>

## <a name="see-also"></a><span data-ttu-id="827a6-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="827a6-129">See also</span></span>

- [<span data-ttu-id="827a6-130">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="827a6-130">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
