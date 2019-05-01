---
title: Hangi yönetilen kod?
description: Yönetilen kod öğrenin, yürütme bir çalışma zamanı tarafından ortak dil çalışma zamanı (CLR) yönetilen koddur.
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 20bb7ea8-192e-4a96-8ef3-e10e1950fd3d
ms.openlocfilehash: 9133859bd9c999e076effcf0d4d631c59db02f33
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910123"
---
# <a name="what-is-managed-code"></a>Nedir "yönetilen kod"?

.NET Framework ile çalışırken, terimi sıklıkla karşılaşır "yönetilen kod". Bu belgede bu terim ne anlama geldiğini ve çevresinde ek bilgiler açıklanmaktadır.

Çok basit geçirmek için yönetilen kod yalnızca olmasıdır: olan yürütme çalışma zamanı tarafından yönetilen kod. Bu durumda, söz konusu çalışma zamanı çağrılır **ortak dil çalışma zamanı** veya CLR, uygulama bağımsız olarak ([Mono](https://www.mono-project.com/) veya .NET Framework veya .NET Core). CLR, yönetilen kodu alma, makine kodu derleme ve ardından yürütme sorumlu olan. Üzerinde çalışma zamanı birkaç sağlayan güvenlik sınırları otomatik bellek yönetimi gibi önemli Hizmetleri tür güvenliği vs.

Bunu, "yönetilmeyen kodun" olarak da bilinir, bir C/C++ programı çalıştıracağınız şekilde karşılaştırın. Yönetilmeyen dünyasında, programcı neredeyse her şeyi sorumlu olur. Gerçek program esas olarak, işletim sistemi (OS) belleğine yükler ve başlatan bir ikili dosyadır. Bellek yönetimi için güvenlik konuları, diğer her şey bir yük programcının kararına olan.

Yönetilen kod gibi .NET üzerinde çalıştırılabilir kullanışını birinde yazılır C#, Visual Basic F# ve diğerleri. Kendi ilgili derleyici ile bu dillerde yazılmış kodu derlediğinizde, makine kodu elde etmezsiniz. Size **Ara dil** derler ve çalıştırır daha sonra çalışma zamanı kodu. C++ Windows üzerinde çalışan yerel, yönetilmeyen ikili dosyaları oluşturabilir bu kuralın tek özel durumu aynıdır.

## <a name="intermediate-language--execution"></a>Ara dil ve yürütme

"Ara dili" (veya kısaca IL) nedir? Üst düzey .NET dillerinde yazılan kod derlemesinin bir üründür. Bir kez yazılan bu dillerden birinde IL dışında yapılan bir ikili erişmenizi sağlayacak kodunuzu derleyin. IL çalışma zamanı üzerinde çalışan herhangi belirli bir dilden bağımsız olduğunu unutmayın; bile, bu nedenle yazmaya, okuyabileceği, için ayrı bir belirtim yoktur.

Üst düzey kodunuzdan IL üretmek sonra çalıştırmak büyük olasılıkla isteyeceksiniz. CLR burada devreye girer ve işlemine başlar **Just-ın-Time** derleme, veya **JIT-ing** IL kodunuzdan makine koduna, gerçekten CPU üzerinde çalıştırılabilir. Bu şekilde, CLR tam olarak, kodunuzun ne yaptığını bilir ve etkili bir şekilde yapabilirsiniz _yönetme_ bu.

Ara dil, bazen de ortak Ara dil (CIL) veya Microsoft Ara dil (MSIL) denir.

## <a name="unmanaged-code-interoperability"></a>Yönetilmeyen kod birlikte çalışabilirliği

Elbette, yönetilen ve yönetilmeyen dünya sınırları geçirme CLR sağlar ve birçok yapan, bile kod [temel sınıf kitaplıkları](framework-libraries.md). Bu adlandırılır **birlikte çalışabilirlik** veya yalnızca **Interop** kısaca. Bu hükümler, örneğin, yönetilmeyen bir kitaplığı sarmalayın ve içine çağırmak çalıştırmasına olanak tanır. Ancak, kod çalışma zamanının sınırlarını geçtiğinde, bunu yaptıktan sonra yürütme yönetimini yeniden yönetilmeyen kod el ile ve bu nedenle aynı kısıtlamalara altında düştüğünde olduğunu unutmayın.

Buna benzer C# olarak bilinen yararlanarak doğrudan kod içinde yönetilmeyen yapıları işaretçi gibi kullanmanıza olanak sağlayan bir dil **güvenli olmayan bir bağlam** kendisi için yürütme yönetilmiyor kod parçasını belirler CLR tarafından.

## <a name="more-resources"></a>Daha fazla kaynak

* [.NET Framework'ün genel bakış](../framework/get-started/overview.md)
* [Güvenli Olmayan Kod ve İşaretçiler](../../docs/csharp/programming-guide/unsafe-code-pointers/index.md)
* [Native ile birlikte çalışma](./native-interop/index.md)
