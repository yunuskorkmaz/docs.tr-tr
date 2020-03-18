---
title: Yerel birlikte çalışabilirlik - .NET
description: .NET'te yerel bileşenlerle nasıl arayüz arayla iletişim etobur sunmayı öğrenin.
ms.date: 01/18/2019
ms.openlocfilehash: 330466d74cc268214f74c4f575e6a2961f678972
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75706341"
---
# <a name="native-interoperability"></a><span data-ttu-id="b486f-103">Native ile birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="b486f-103">Native interoperability</span></span>

<span data-ttu-id="b486f-104">Aşağıdaki makaleler .NET'te "yerel birlikte çalışabilirlik" yapmanın çeşitli yollarını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="b486f-104">The following articles show the various ways of doing "native interoperability" in .NET.</span></span>

<span data-ttu-id="b486f-105">Yerel kodu aramak istemenizin birkaç nedeni vardır:</span><span class="sxs-lookup"><span data-stu-id="b486f-105">There are a few reasons why you'd want to call into native code:</span></span>

- <span data-ttu-id="b486f-106">İşletim sistemleri, yönetilen sınıf kitaplıklarında bulunmayan büyük hacimli API'lerle birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="b486f-106">Operating systems come with a large volume of APIs that aren't present in the managed class libraries.</span></span> <span data-ttu-id="b486f-107">Bu senaryo için en önemli örnek donanım veya işletim sistemi yönetim işlevlerine erişim olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b486f-107">A prime example for this scenario would be access to hardware or operating system management functions.</span></span>
- <span data-ttu-id="b486f-108">[Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) veya yerel bir bileşen oluşturabilecek başka bir yönetilen dil aracılığıyla ortaya çıkarılan Java kodu gibi C stili ABI'leri (yerel ABI' ler) olan veya üretebilen diğer bileşenlerle iletişim kurmak.</span><span class="sxs-lookup"><span data-stu-id="b486f-108">Communicating with other components that have or can produce C-style ABIs (native ABIs), such as Java code that is exposed via [Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) or any other managed language that could produce a native component.</span></span>
- <span data-ttu-id="b486f-109">Windows'da, Microsoft Office paketi gibi yüklenen yazılımların çoğu, programlarını temsil eden ve geliştiricilerin bunları otomatikleştirmesine veya kullanmasına izin veren COM bileşenlerini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="b486f-109">On Windows, most of the software that gets installed, such as the Microsoft Office suite, registers COM components that represent their programs and allow developers to automate them or use them.</span></span> <span data-ttu-id="b486f-110">Bu da yerel birlikte çalışabilirlik gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b486f-110">This also requires native interoperability.</span></span>

<span data-ttu-id="b486f-111">Önceki liste, geliştiricinin yerel bileşenlerle ara birim yapmak istediği/beğeneceği/ihtiyaç dalacağı tüm olası durumları ve senaryoları kapsamaz.</span><span class="sxs-lookup"><span data-stu-id="b486f-111">The previous list doesn't cover all of the potential situations and scenarios in which the developer would want/like/need to interface with native components.</span></span> <span data-ttu-id="b486f-112">.NET sınıf kitaplığı, örneğin, konsol desteği ve manipülasyon, dosya sistemi erişimi ve diğerleri gibi adil sayıda API'sini uygulamak için yerel birlikte çalışabilirlik desteğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b486f-112">.NET class library, for instance, uses the native interoperability support to implement a fair number of its APIs, like console support and manipulation, file system access and others.</span></span> <span data-ttu-id="b486f-113">Ancak, gerekirse bir seçenek olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b486f-113">However, it's important to note that there's an option if needed.</span></span>

> [!NOTE]
> <span data-ttu-id="b486f-114">Bu bölümdeki örneklerin çoğu .NET Core (Windows, Linux ve macOS) için desteklenen üç platform için de sunulacaktır.</span><span class="sxs-lookup"><span data-stu-id="b486f-114">Most of the examples in this section will be presented for all three supported platforms for .NET Core (Windows, Linux and macOS).</span></span> <span data-ttu-id="b486f-115">Ancak, bazı kısa ve açıklayıcı örnekler için, Windows dosya adlarını ve uzantılarını kullanan tek bir örnek gösterilir (diğer bir şekilde kitaplıklar için "dll").</span><span class="sxs-lookup"><span data-stu-id="b486f-115">However, for some short and illustrative examples, just one sample is shown that uses Windows filenames and extensions (that is, "dll" for libraries).</span></span> <span data-ttu-id="b486f-116">Bu bu özellikleri Linux veya macOS mevcut olmadığı anlamına gelmez, sadece kolaylık uğruna yapıldı.</span><span class="sxs-lookup"><span data-stu-id="b486f-116">This doesn't mean that those features aren't available on Linux or macOS, it was done merely for convenience sake.</span></span>

## <a name="see-also"></a><span data-ttu-id="b486f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b486f-117">See also</span></span>

- [<span data-ttu-id="b486f-118">Platform Çağırma (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="b486f-118">Platform Invoke (P/Invoke)</span></span>](pinvoke.md)
- [<span data-ttu-id="b486f-119">Tür hazırlama</span><span class="sxs-lookup"><span data-stu-id="b486f-119">Type marshaling</span></span>](type-marshaling.md)
- [<span data-ttu-id="b486f-120">Yerel birlikte çalışabilirlik en iyi uygulamalar</span><span class="sxs-lookup"><span data-stu-id="b486f-120">Native interoperability best practices</span></span>](best-practices.md)
