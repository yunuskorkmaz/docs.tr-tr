---
title: Yönetilen kod nedir?
description: Yönetilen kodun, yürütmesi çalışma zamanı olan Ortak Dil Çalışma Zamanı (CLR) tarafından yönetilen kod olduğunu öğrenin.
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 20bb7ea8-192e-4a96-8ef3-e10e1950fd3d
ms.openlocfilehash: 9133859bd9c999e076effcf0d4d631c59db02f33
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "61910123"
---
# <a name="what-is-managed-code"></a>“Yönetilen kod” nedir?

.NET Framework ile çalışırken sık sık "yönetilen kod" terimiyle karşılaşırsınız. Bu belge, bu terimin ne anlama geldiğini ve çevresinde ek bilgiler açıklayacaktır.

Çok basit bir ifadeyle, yönetilen kod sadece şudur: yürütmesi bir çalışma zamanı tarafından yönetilen kod. Bu durumda, söz konusu çalışma süresi, uygulamadan bağımsız olarak[(Mono](https://www.mono-project.com/) veya .NET Framework veya .NET Core) **Ortak Dil Çalışma Süresi** veya CLR olarak adlandırılır. CLR, yönetilen kodu almaktan, makine koduna derlemekten ve daha sonra yürütmekten sorumludur. Bunun üzerine, çalışma süresi otomatik bellek yönetimi, güvenlik sınırları, tip güvenliği vb. gibi birçok önemli hizmeti sağlar.

Bunu, "yönetilmeyen kod" olarak da adlandırılan bir C/C++ programını çalıştırma şeklinizle karşılaştırın. Yönetilmeyen dünyada, programcı hemen hemen her şeyden sorumludur. Gerçek program, aslında, bir ikili işletim sistemi (OS) bellek içine yükler ve başlar. Bellek yönetiminden güvenlik konularına kadar her şey programcının yükündedir.

Yönetilen kod, C#, Visual Basic, F# ve diğerleri gibi .NET'in üstünde çalıştırılabilen üst düzey dillerden birinde yazılır. Bu dillerde kendi derleyicileriyle yazılmış kodları derlediğinizde, makine kodu alamazsınız. Çalışma zamanının derlediği ve çalıştırdığı **Ara Dil** kodunu alırsınız. C++ bu kuralın tek istisnasıdır, çünkü Windows'ta çalışan yerel, yönetilmeyen ikili ler de üretebilir.

## <a name="intermediate-language--execution"></a>Orta Dil & yürütme

"Orta Dil" (veya kısaca IL) nedir? Üst düzey .NET dillerinde yazılmış kodun bir derleme ürünüdür. Bu dillerden birinde yazılmış kodunuzu derledikten sonra, IL'den yapılmış bir ikili alırsınız. IL'nin çalışma zamanının üstünde çalışan herhangi bir dilden bağımsız olduğunu unutmayın; eğer çok eğimli iseniz okuyabilirsiniz bunun için ayrı bir belirtim bile vardır.

Üst düzey kodunuzdan IL'yi ürettiğinizde, büyük olasılıkla çalıştırmak isteyeceksiniz. Burası CLR'nin devreye girip **Just-In-Time** derleme işlemini başlattığı veya kodunuzu IL'den cpu üzerinde çalıştırılabilen makine koduna **jit-ing** işlemini başlattığı yerdir. Bu şekilde, CLR kodunuzun tam olarak ne yaptığını bilir ve etkili bir şekilde _yönetebilir._

Ara Dil bazen Ortak Ara Dil (CIL) veya Microsoft Intermediate Language (MSIL) olarak da adlandırılır.

## <a name="unmanaged-code-interoperability"></a>Yönetilmeyen kod birlikte çalışabilirliği

Tabii ki, CLR yönetilen ve yönetilmeyen dünya arasındaki sınırları geçen sağlar ve [base class kütüphaneleri](framework-libraries.md)bile, bunu kod bir yeri vardır. Buna **birlikte çalışabilirlik** ya da kısaca **interop** denir. Bu hükümler, örneğin, yönetilmeyen bir kitaplığı tamamlamanızı ve bu kitapiçin aramanızı sağlar. Ancak, bunu yaptığınızda, kod çalışma zamanının sınırlarını geçtiğinde, yürütmenin gerçek yönetiminin yine yönetilmeyen kodun elinde olduğunu ve böylece aynı kısıtlamalar altında kaldığını unutmayın.

Buna benzer şekilde, C# yürütme CLR tarafından yönetilmeyen bir kod parçası belirleyen güvenli olmayan **bağlam** olarak bilinen kullanarak doğrudan kod işaretçileri gibi yönetilmeyen yapıları kullanmanızı sağlayan bir dildir.

## <a name="more-resources"></a>Diğer kaynaklar

* [.NET Framework'e Genel Bakış](../framework/get-started/overview.md)
* [Güvenli Olmayan Kod ve İşaretçiler](../../docs/csharp/programming-guide/unsafe-code-pointers/index.md)
* [Yerel birlikte çalışabilirlik](./native-interop/index.md)
