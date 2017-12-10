---
title: "Hangi yönetilen kodu?"
description: "Yönetilen kod öğrenin, yürütme bir çalışma zamanı tarafından ortak dil çalışma zamanı (CLR) yönetilen kodudur."
keywords: .NET, .NET core
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 20bb7ea8-192e-4a96-8ef3-e10e1950fd3d
ms.openlocfilehash: 8649402e614f07a611947302d14e05108e1cc171
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="what-is-managed-code"></a>Nedir "yönetilen kod"?

.NET Framework ile çalışırken, terimi genellikle karşılaşır "yönetilen kod". Bu belgede, bu terim ne anlama geldiğini ve ek bilgiler çevresinde anlatılmıştır.

Bu çok basitçe, yönetilen kod yalnızca olan:, yürütme çalışma zamanı tarafından yönetilen kod. Bu durumda, söz konusu çalışma zamanı adlı **ortak dil çalışma zamanı** veya uygulamadan bağımsız olarak CLR ([Mono](http://www.mono-project.com/) veya .NET Framework veya .NET Core). CLR yönetilen kod alma, makine koda derleme ve, yürütülmekte sorumlu içindir. En üstünde, çalışma zamanı birkaç sağlayan otomatik bellek yönetimi, güvenlik sınırları gibi önemli hizmetler güvenliği vb. yazın.

Bunu, "yönetilmeyen kod" olarak da adlandırılan bir C/C++ programı çalıştırılır şekilde karşılaştırın. Yönetilmeyen dünyada Programcı neredeyse her şeyi sorumlu olur. Gerçek program esas olarak, işletim sistemi (OS) belleğe yükleyen ve başlatan bir ikili dosyadır. Bellek yönetimi için güvenlik konuları başka her şey Programcı yükünü olan.

Yönetilen kod C#, Visual Basic, F # ve diğerleri gibi .NET üzerinde çalıştırılabilir üst düzey dillerden biriyle yazılır. Bu dillerde kendi ilgili derleyicisi ile yazılan kod derleme yaparken makine kodu almadım. Aldığınız **Ara dile** çalışma zamanı sonra derleyen ve yürütür kodu. C++ bu kural için bir özel aynıdır Windows üzerinde çalışan yerel, yönetilmeyen ikili dosyaları üretebilir.

## <a name="intermediate-language--execution"></a>Ara dil ve yürütme

"Ara dil" (veya kısaca IL) nedir? Üst düzey .NET dilinde yazılan kod derlenmesini ürünüdür. Bir kez yazılmış bu dillerden birinde IL dışında yapılan bir ikili alırsınız kodunuzu derleyin. IL çalışma zamanı en üstünde çalışan herhangi belirli bir dilden bağımsız olduğunu dikkate almak önemlidir; Bunu, bu nedenle inclined varsa okuyabilir için ayrı bir belirtimi bile yoktur.

Üst düzey kodunuzdan IL üretmek sonra büyük olasılıkla çalıştırmak isteyeceksiniz. Burada CLR devreye girer ve işlemini başlatır budur **zaman içinde sadece** derleme, veya **JIT lık** IL kodunuzdan gerçekte bir CPU üzerinde çalıştırılabilir makine kodu. Bu şekilde, CLR kodunuzu tam olarak yaptıklarını bilir ve etkili bir şekilde yapabilirsiniz _yönetmek_ onu.

Ara dil bazen de ortak Ara dili (CIL) veya Microsoft Ara dili (MSIL) denir.

## <a name="unmanaged-code-interoperability"></a>Yönetilmeyen kod birlikte çalışabilirliği

Elbette, CLR sınırlar arasında yönetilen ve yönetilmeyen world sağlar ve çok, bile yapan kod [temel sınıf kitaplıkları](framework-libraries.md). Bu adlı **birlikte çalışabilirlik** veya yalnızca **birlikte çalışabilirliği** kısaca. Bu hükümleri, örneğin, bir yönetilmeyen kitaplığı kaydırma ve içine çağrı olanak tanır. Bununla birlikte, kod sınırları çalışma zamanının başarılı olduğunda, bunu yaptığınızda, yürütme gerçek yönetim yeniden yönetilmeyen kod el ile ve bu nedenle aynı kısıtlamalara altında kalan olduğunu dikkate almak önemlidir.

Bu, C# olarak bilinen yararlanarak doğrudan kodunda işaretçileri gibi yönetilmeyen yapılar kullanmanıza olanak sağlayan bir dil benzer **güvenli olmayan içerik** paylaştırılabilen bir kod için yürütme yönetilmiyor tarafından belirler CLR.

## <a name="more-resources"></a>Daha fazla kaynak

*   [.NET framework kavramsal genel bakış](https://msdn.microsoft.com/library/zw4w595w.aspx)
*   [Güvenli olmayan kod ve işaretçiler](../../docs/csharp/programming-guide/unsafe-code-pointers/index.md)
*   [Birlikte çalışabilirlik (C# programlama Kılavuzu)](https://msdn.microsoft.com/library/ms173184.aspx)
