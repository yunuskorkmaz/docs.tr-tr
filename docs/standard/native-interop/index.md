---
title: Yerel birlikte çalışabilirlik-.NET
description: .NET ' te yerel bileşenlerle arabirim oluşturmayı öğrenin.
ms.date: 01/18/2019
ms.openlocfilehash: 330466d74cc268214f74c4f575e6a2961f678972
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706341"
---
# <a name="native-interoperability"></a><span data-ttu-id="4bcd6-103">Native ile birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="4bcd6-103">Native interoperability</span></span>

<span data-ttu-id="4bcd6-104">Aşağıdaki makalelerde .NET içinde "yerel birlikte çalışabilirlik" yapmanın çeşitli yolları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4bcd6-104">The following articles show the various ways of doing "native interoperability" in .NET.</span></span>

<span data-ttu-id="4bcd6-105">Yerel koda çağrı yapmak istemenizin birkaç nedeni vardır:</span><span class="sxs-lookup"><span data-stu-id="4bcd6-105">There are a few reasons why you'd want to call into native code:</span></span>

- <span data-ttu-id="4bcd6-106">İşletim sistemleri, yönetilen sınıf kitaplıklarında bulunmayan büyük bir API hacimiyle gelir.</span><span class="sxs-lookup"><span data-stu-id="4bcd6-106">Operating systems come with a large volume of APIs that aren't present in the managed class libraries.</span></span> <span data-ttu-id="4bcd6-107">Bu senaryo için bir ana örnek, donanım veya işletim sistemi yönetim işlevlerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="4bcd6-107">A prime example for this scenario would be access to hardware or operating system management functions.</span></span>
- <span data-ttu-id="4bcd6-108">[Java Native Interface (JNı)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) aracılığıyla veya yerel bir bileşen oluşturabilecek başka bir yönetilen dilde sunulan Java kodu gibi C stili ABR 'leri (yerel absıs) oluşturan veya üreten diğer bileşenlerle iletişim kurma.</span><span class="sxs-lookup"><span data-stu-id="4bcd6-108">Communicating with other components that have or can produce C-style ABIs (native ABIs), such as Java code that is exposed via [Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) or any other managed language that could produce a native component.</span></span>
- <span data-ttu-id="4bcd6-109">Windows 'da, Microsoft Office Suite gibi yüklü yazılımların çoğu, programlarını temsil eden COM bileşenlerini kaydettirir ve geliştiricilerin bunları otomatikleştirebilmeleri veya onları kullanmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="4bcd6-109">On Windows, most of the software that gets installed, such as the Microsoft Office suite, registers COM components that represent their programs and allow developers to automate them or use them.</span></span> <span data-ttu-id="4bcd6-110">Bu, yerel birlikte çalışabilirlik de gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4bcd6-110">This also requires native interoperability.</span></span>

<span data-ttu-id="4bcd6-111">Önceki listede, geliştiricinin yerel bileşenlerle arabirim istediğini/beğenmek istediği tüm olası durumlar ve senaryolar ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4bcd6-111">The previous list doesn't cover all of the potential situations and scenarios in which the developer would want/like/need to interface with native components.</span></span> <span data-ttu-id="4bcd6-112">.NET sınıf kitaplığı, örneğin, konsol desteği ve işleme, dosya sistemi erişimi ve diğerleri gibi API 'Lerinin bir dengeli sayısını uygulamak için yerel birlikte çalışabilirlik desteğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="4bcd6-112">.NET class library, for instance, uses the native interoperability support to implement a fair number of its APIs, like console support and manipulation, file system access and others.</span></span> <span data-ttu-id="4bcd6-113">Ancak, gerekirse bir seçenek olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="4bcd6-113">However, it's important to note that there's an option if needed.</span></span>

> [!NOTE]
> <span data-ttu-id="4bcd6-114">Bu bölümdeki örneklerin çoğu, .NET Core için desteklenen üç platformda (Windows, Linux ve macOS) sunulacak.</span><span class="sxs-lookup"><span data-stu-id="4bcd6-114">Most of the examples in this section will be presented for all three supported platforms for .NET Core (Windows, Linux and macOS).</span></span> <span data-ttu-id="4bcd6-115">Ancak bazı Short ve tanım örneklerinde, Windows dosya adları ve uzantıları kullanan tek bir örnek gösterilir (yani, kitaplıklar için "dll").</span><span class="sxs-lookup"><span data-stu-id="4bcd6-115">However, for some short and illustrative examples, just one sample is shown that uses Windows filenames and extensions (that is, "dll" for libraries).</span></span> <span data-ttu-id="4bcd6-116">Bu, bu özelliklerin Linux veya macOS üzerinde kullanılamadığı anlamına gelmez, ancak kolay bir sake için yapılmıştı.</span><span class="sxs-lookup"><span data-stu-id="4bcd6-116">This doesn't mean that those features aren't available on Linux or macOS, it was done merely for convenience sake.</span></span>

## <a name="see-also"></a><span data-ttu-id="4bcd6-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4bcd6-117">See also</span></span>

- [<span data-ttu-id="4bcd6-118">Platform çağırma (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="4bcd6-118">Platform Invoke (P/Invoke)</span></span>](pinvoke.md)
- [<span data-ttu-id="4bcd6-119">Tür sıralaması</span><span class="sxs-lookup"><span data-stu-id="4bcd6-119">Type marshaling</span></span>](type-marshaling.md)
- [<span data-ttu-id="4bcd6-120">Yerel birlikte çalışabilirlik en iyi uygulamaları</span><span class="sxs-lookup"><span data-stu-id="4bcd6-120">Native interoperability best practices</span></span>](best-practices.md)
