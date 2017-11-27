---
title: "Tür Sağlayıcısı Güvenliği"
description: "F tür sağlayıcısı güven ayarlarını değiştirmek nasıl dahil olmak üzere #, tür sağlayıcısı güvenliği hakkında bilgi edinin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9c5a8a1f-5a31-490d-83c0-8beabda75c78
ms.openlocfilehash: c8f03ee90d4dce1d3484a9dfe8951d500d509a2b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="type-provider-security"></a><span data-ttu-id="60d6b-104">Tür Sağlayıcısı Güvenliği</span><span class="sxs-lookup"><span data-stu-id="60d6b-104">Type Provider Security</span></span>

<span data-ttu-id="60d6b-105">Türü, dış veri kaynaklarına bağlanmak ve bu tür bilgiler F # türü ortamına yüzey için kod içeren F # proje veya komut dosyası tarafından başvurulan derlemeler (dll) sağlayıcılarıdır.</span><span class="sxs-lookup"><span data-stu-id="60d6b-105">Type providers are assemblies (DLLs) referenced by your F# project or script that contain code to connect to external data sources and surface this type information to the F# type environment.</span></span> <span data-ttu-id="60d6b-106">Genellikle, derleyin ve ardından kod yürütmek (veya bir komut dosyası söz konusu olduğunda kodu F # Etkileşimli'ye gönderdiğinizde) başvurulan derlemelerin kodda yalnızca çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="60d6b-106">Typically, code in referenced assemblies is only run when you compile and then execute the code (or in the case of a script, send the code to F# Interactive).</span></span> <span data-ttu-id="60d6b-107">Bununla birlikte, Kod düzenleyicisinde yalnızca gözatarken türü sağlayıcı derlemesi Visual Studio içinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="60d6b-107">However, a type provider assembly will run inside Visual Studio when the code is merely browsed in the editor.</span></span> <span data-ttu-id="60d6b-108">Tür sağlayıcıları hızlı bilgi araç ipuçlarını, IntelliSense tamamlamalar gibi Düzenleyicisi ek bilgi eklemek üzere çalıştırmanız gerekir çünkü bu gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="60d6b-108">This happens because type providers need to run to add extra information to the editor, such as Quick Info tooltips, IntelliSense completions, and so on.</span></span> <span data-ttu-id="60d6b-109">Sonuç olarak, ek güvenlik noktalar vardır türü için sağlayıcı derlemeleri, Visual Studio işlemi içinde otomatik olarak çalıştırdıkları beri.</span><span class="sxs-lookup"><span data-stu-id="60d6b-109">As a result, there are extra security considerations for type provider assemblies, since they run automatically inside the Visual Studio process.</span></span>


## <a name="security-warning-dialog"></a><span data-ttu-id="60d6b-110">Güvenlik Uyarısı iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="60d6b-110">Security Warning Dialog</span></span>
<span data-ttu-id="60d6b-111">Bir türdeki sağlayıcı derlemesi ilk kez kullanırken, Visual Studio, tür sağlayıcısı çalışmak üzere olduğunu sizi uyarır güvenlik iletişim kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="60d6b-111">When using a particular type provider assembly for the first time, Visual Studio displays a security dialog that warns you that the type provider is about to run.</span></span> <span data-ttu-id="60d6b-112">Visual Studio türü sağlayıcısı yüklemeden önce bu belirli sağlayıcı güveniyorsanız karar verme olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="60d6b-112">Before Visual Studio loads the type provider, it gives you the opportunity to decide if you trust this particular provider.</span></span> <span data-ttu-id="60d6b-113">Tür sağlayıcısı kaynağına güveniyorsanız, ardından "Bu tür sağlayıcısı güvendiğim." seçin</span><span class="sxs-lookup"><span data-stu-id="60d6b-113">If you trust the source of the type provider, then select "I trust this type provider."</span></span> <span data-ttu-id="60d6b-114">Tür sağlayıcısı kaynağına güvenmiyorsanız, ardından "Bu tür sağlayıcısı güvendiğim değil." seçin</span><span class="sxs-lookup"><span data-stu-id="60d6b-114">If you do not trust the source of the type provider, then select "I do not trust this type provider."</span></span> <span data-ttu-id="60d6b-115">Sağlayıcı güvenen Visual Studio içinde çalıştırmak ve IntelliSense sağlar ve özellikleri oluşturmak için etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="60d6b-115">Trusting the provider enables it to run inside Visual Studio and provide IntelliSense and build features.</span></span> <span data-ttu-id="60d6b-116">Ancak, tür sağlayıcısı kötü amaçlı ise, kendi kod çalıştıran makinenizi güvenliğinin aşılmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="60d6b-116">But if the type provider itself is malicious, running its code could compromise your machine.</span></span>

<span data-ttu-id="60d6b-117">Projenizi güvenmediğiniz için iletişim kutusunda seçtiğiniz tür sağlayıcıları başvuran kodu içeriyorsa, derleme zamanında derleyici tür sağlayıcısı güvenilmeyen olduğunu belirten bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="60d6b-117">If your project contains code that references type providers that you chose in the dialog not to trust, then at compile time, the compiler will report an error that indicates that the type provider is untrusted.</span></span> <span data-ttu-id="60d6b-118">Güvenilmeyen türü sağlayıcısında bağımlı türleri kırmızı dalgalı çizgiler tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="60d6b-118">Any types that are dependent on the untrusted type provider are indicated by red squiggles.</span></span> <span data-ttu-id="60d6b-119">Kod Düzenleyicisi'nde göz atmak güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="60d6b-119">It is safe to browse the code in the editor.</span></span>

<span data-ttu-id="60d6b-120">Visual Studio'da doğrudan güven ayarını değiştirmeye karar verirseniz, aşağıdaki adımları gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="60d6b-120">If you decide to change the trust setting directly in Visual Studio, perform the following steps.</span></span>


#### <a name="to-change-the-trust-settings-for-type-providers"></a><span data-ttu-id="60d6b-121">Tür sağlayıcıları güven ayarlarını değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="60d6b-121">To change the trust settings for type providers</span></span>

1. <span data-ttu-id="60d6b-122">Üzerinde `Tools` menüsünde, select `Options`ve genişletin `F# Tools` düğümü.</span><span class="sxs-lookup"><span data-stu-id="60d6b-122">On the `Tools` menu, select `Options`, and expand the `F# Tools` node.</span></span>
<br />

2. <span data-ttu-id="60d6b-123">Seçin `Type Providers`, tür sağlayıcıları listesinde güvendiğiniz tür sağlayıcıları için onay kutusunu işaretleyin ve güvenmediğiniz olanlar için onay kutusunu temizleyin.</span><span class="sxs-lookup"><span data-stu-id="60d6b-123">Select `Type Providers`, and in the list of type providers, select the check box for type providers you trust, and clear the check box for those you don't trust.</span></span>
<br />


## <a name="see-also"></a><span data-ttu-id="60d6b-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="60d6b-124">See Also</span></span>
[<span data-ttu-id="60d6b-125">Tür sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="60d6b-125">Type Providers</span></span>](index.md)
