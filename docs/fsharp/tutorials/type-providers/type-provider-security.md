---
title: Tür Sağlayıcısı Güvenliği
description: 'F tür sağlayıcısı güven ayarlarını değiştirmek nasıl dahil olmak üzere #, tür sağlayıcısı güvenliği hakkında bilgi edinin.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 4f0b55062aec6c560112fe10ca4df77f42493011
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="type-provider-security"></a><span data-ttu-id="0d282-103">Tür Sağlayıcısı Güvenliği</span><span class="sxs-lookup"><span data-stu-id="0d282-103">Type Provider Security</span></span>

<span data-ttu-id="0d282-104">Türü, dış veri kaynaklarına bağlanmak ve bu tür bilgiler F # türü ortamına yüzey için kod içeren F # proje veya komut dosyası tarafından başvurulan derlemeler (dll) sağlayıcılarıdır.</span><span class="sxs-lookup"><span data-stu-id="0d282-104">Type providers are assemblies (DLLs) referenced by your F# project or script that contain code to connect to external data sources and surface this type information to the F# type environment.</span></span> <span data-ttu-id="0d282-105">Genellikle, derleyin ve ardından kod yürütmek (veya bir komut dosyası söz konusu olduğunda kodu F # Etkileşimli'ye gönderdiğinizde) başvurulan derlemelerin kodda yalnızca çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="0d282-105">Typically, code in referenced assemblies is only run when you compile and then execute the code (or in the case of a script, send the code to F# Interactive).</span></span> <span data-ttu-id="0d282-106">Bununla birlikte, Kod düzenleyicisinde yalnızca gözatarken türü sağlayıcı derlemesi Visual Studio içinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="0d282-106">However, a type provider assembly will run inside Visual Studio when the code is merely browsed in the editor.</span></span> <span data-ttu-id="0d282-107">Tür sağlayıcıları hızlı bilgi araç ipuçlarını, IntelliSense tamamlamalar gibi Düzenleyicisi ek bilgi eklemek üzere çalıştırmanız gerekir çünkü bu gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="0d282-107">This happens because type providers need to run to add extra information to the editor, such as Quick Info tooltips, IntelliSense completions, and so on.</span></span> <span data-ttu-id="0d282-108">Sonuç olarak, ek güvenlik noktalar vardır türü için sağlayıcı derlemeleri, Visual Studio işlemi içinde otomatik olarak çalıştırdıkları beri.</span><span class="sxs-lookup"><span data-stu-id="0d282-108">As a result, there are extra security considerations for type provider assemblies, since they run automatically inside the Visual Studio process.</span></span>


## <a name="security-warning-dialog"></a><span data-ttu-id="0d282-109">Güvenlik Uyarısı iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="0d282-109">Security Warning Dialog</span></span>
<span data-ttu-id="0d282-110">Bir türdeki sağlayıcı derlemesi ilk kez kullanırken, Visual Studio, tür sağlayıcısı çalışmak üzere olduğunu sizi uyarır güvenlik iletişim kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0d282-110">When using a particular type provider assembly for the first time, Visual Studio displays a security dialog that warns you that the type provider is about to run.</span></span> <span data-ttu-id="0d282-111">Visual Studio türü sağlayıcısı yüklemeden önce bu belirli sağlayıcı güveniyorsanız karar verme olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="0d282-111">Before Visual Studio loads the type provider, it gives you the opportunity to decide if you trust this particular provider.</span></span> <span data-ttu-id="0d282-112">Tür sağlayıcısı kaynağına güveniyorsanız, ardından "Bu tür sağlayıcısı güvendiğim." seçin</span><span class="sxs-lookup"><span data-stu-id="0d282-112">If you trust the source of the type provider, then select "I trust this type provider."</span></span> <span data-ttu-id="0d282-113">Tür sağlayıcısı kaynağına güvenmiyorsanız, ardından "Bu tür sağlayıcısı güvendiğim değil." seçin</span><span class="sxs-lookup"><span data-stu-id="0d282-113">If you do not trust the source of the type provider, then select "I do not trust this type provider."</span></span> <span data-ttu-id="0d282-114">Sağlayıcı güvenen Visual Studio içinde çalıştırmak ve IntelliSense sağlar ve özellikleri oluşturmak için etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="0d282-114">Trusting the provider enables it to run inside Visual Studio and provide IntelliSense and build features.</span></span> <span data-ttu-id="0d282-115">Ancak, tür sağlayıcısı kötü amaçlı ise, kendi kod çalıştıran makinenizi güvenliğinin aşılmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="0d282-115">But if the type provider itself is malicious, running its code could compromise your machine.</span></span>

<span data-ttu-id="0d282-116">Projenizi güvenmediğiniz için iletişim kutusunda seçtiğiniz tür sağlayıcıları başvuran kodu içeriyorsa, derleme zamanında derleyici tür sağlayıcısı güvenilmeyen olduğunu belirten bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="0d282-116">If your project contains code that references type providers that you chose in the dialog not to trust, then at compile time, the compiler will report an error that indicates that the type provider is untrusted.</span></span> <span data-ttu-id="0d282-117">Güvenilmeyen türü sağlayıcısında bağımlı türleri kırmızı dalgalı çizgiler tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="0d282-117">Any types that are dependent on the untrusted type provider are indicated by red squiggles.</span></span> <span data-ttu-id="0d282-118">Kod Düzenleyicisi'nde göz atmak güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="0d282-118">It is safe to browse the code in the editor.</span></span>

<span data-ttu-id="0d282-119">Visual Studio'da doğrudan güven ayarını değiştirmeye karar verirseniz, aşağıdaki adımları gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="0d282-119">If you decide to change the trust setting directly in Visual Studio, perform the following steps.</span></span>


#### <a name="to-change-the-trust-settings-for-type-providers"></a><span data-ttu-id="0d282-120">Tür sağlayıcıları güven ayarlarını değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="0d282-120">To change the trust settings for type providers</span></span>

1. <span data-ttu-id="0d282-121">Üzerinde `Tools` menüsünde, select `Options`ve genişletin `F# Tools` düğümü.</span><span class="sxs-lookup"><span data-stu-id="0d282-121">On the `Tools` menu, select `Options`, and expand the `F# Tools` node.</span></span>
<br />

2. <span data-ttu-id="0d282-122">Seçin `Type Providers`, tür sağlayıcıları listesinde güvendiğiniz tür sağlayıcıları için onay kutusunu işaretleyin ve güvenmediğiniz olanlar için onay kutusunu temizleyin.</span><span class="sxs-lookup"><span data-stu-id="0d282-122">Select `Type Providers`, and in the list of type providers, select the check box for type providers you trust, and clear the check box for those you don't trust.</span></span>
<br />


## <a name="see-also"></a><span data-ttu-id="0d282-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0d282-123">See Also</span></span>
[<span data-ttu-id="0d282-124">Tür Sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="0d282-124">Type Providers</span></span>](index.md)
