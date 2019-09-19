---
title: 'Nasıl yapılır: Birincil Birlikte Çalışma Derlemelerini Kaydetme'
ms.date: 03/30/2017
helpviewer_keywords:
- registering primary interop assemblies
- primary interop assemblies, registering
ms.assetid: 4b2fcf8a-429d-43ce-8334-e026040be8bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e0eeaee969eda5e4d0ea1a119991456668c7d44f
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051736"
---
# <a name="how-to-register-primary-interop-assemblies"></a>Nasıl yapılır: Birincil Birlikte Çalışma Derlemelerini Kaydetme

Sınıflar yalnızca COM birlikte çalışabilirliğine göre sıralanabilir ve her zaman arabirim olarak sıralanır. Bazı durumlarda, sınıfı sıralamak için kullanılan arabirim sınıf arabirimi olarak bilinir. Sınıf arabirimini tercih ettiğiniz bir arabirimle geçersiz kılma hakkında daha fazla bilgi için bkz. [com çağrılabilir sarmalayıcı](../../standard/native-interop/com-callable-wrapper.md).

 .NET Framework bir uygulamadan COM türlerini kullanmak isteyen herhangi bir geliştirici birlikte çalışma derlemesi oluşturabileceğinden, bu durum bir sorun oluşturur. Bir geliştirici bir COM tür kitaplığını içeri aktardığında ve imzaladığında, bu geliştirici, içeri aktarılan ve başka bir geliştirici tarafından imzalanan bir benzersiz türler kümesi oluşturur. Bu tür uyumsuzluk sorununa yönelik çözüm, her geliştiricinin satıcı tarafından sağlanan ve imzalı birincil birlikte çalışma derlemesini edinmesine yöneliktir.

 Üçüncü taraf COM türlerini diğer uygulamalar için kullanıma sunmayı planlıyorsanız, her zaman tanımladığı tür kitaplığıyla aynı yayımcı tarafından sunulan birincil birlikte çalışma derlemesini kullanın. Garantili tür uyumluluğu sağlamanın yanı sıra, birincil birlikte çalışma derlemeleri genellikle birlikte çalışabilirliği iyileştirmek için satıcı tarafından özelleştirilir.

 Üçüncü taraf COM türlerini açığa çıkarmak için planlamasanız bile, birincil birlikte çalışma derlemesini kullanmak COM bileşenleriyle birlikte çalışma görevini kolaylaştırabilir. Ancak, bu strateji, bir satıcının birincil birlikte çalışma derlemesinde tanımlı türler üzerinde yapabildikleri değişikliklerden ayrı bir işlem sağlar. Uygulamanız bu tür yalıtımı gerektirdiğinde, birincil birlikte çalışma derlemesini kullanmak yerine kendi birlikte çalışma derlemenizi oluşturun.

 Visual Studio ile başvurmadan önce, satın alınan tüm birincil birlikte çalışma derlemelerini geliştirme bilgisayarınıza kaydetmeniz gerekir. Visual Studio, bir COM tür kitaplığından bir türe ilk kez başvurduğunuzda bir birincil birlikte çalışma derlemesini arar ve kullanır. Visual Studio, tür kitaplığıyla ilişkili birincil birlikte çalışma derlemesini bulamıyorsa, bunun yerine bir birlikte çalışma derlemesi oluşturmak için size veya tekliflerini almanızı ister. Benzer şekilde, [tür kitaplığı alma programı (Tlbimp. exe)](../tools/tlbimp-exe-type-library-importer.md) , birincil birlikte çalışma derlemelerini bulmak için kayıt defterini de kullanır.

 Visual Studio 'Yu kullanmayı planlamıyorsanız birincil birlikte çalışma derlemelerini kaydetmek gerekli olmasa da, kayıt iki avantaj sağlar:

- Kayıtlı bir birincil birlikte çalışma derlemesi, özgün tür kitaplığının kayıt defteri anahtarı altında açıkça işaretlenir. Kayıt, bilgisayarınızda bir birincil birlikte çalışma derlemesini bulmanız için en iyi yoldur.

- Yanlışlıkla yeni bir birlikte çalışma derlemesini oluşturmaktan ve kullanmaktan kaçınabilirsiniz. daha sonra, daha sonra, kayıtlı bir birincil birlikte çalışma derlemesine sahip olduğunuz bir türe başvurmak için Visual Studio 'Yu kullanabilirsiniz.

Birincil birlikte çalışma derlemesini kaydetmek için [derleme kayıt aracı 'nı (Regasm. exe)](../tools/regasm-exe-assembly-registration-tool.md) kullanın.

## <a name="to-register-a-primary-interop-assembly"></a>Birincil birlikte çalışma derlemesini kaydetmek için

1. Komut isteminde, şunları yazın:

     **Regasm** *AssemblyName*

     Bu komutta, *AssemblyName* kayıtlı derlemenin dosya adıdır. Regasm. exe, özgün tür kitaplığıyla aynı kayıt defteri anahtarı altında birincil birlikte çalışma derlemesi için bir girdi ekler.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, `CompanyA.UtilLib.dll` birincil birlikte çalışma derlemesini kaydeder.

```console
regasm CompanyA.UtilLib.dll
```

## <a name="see-also"></a>Ayrıca bkz.

- [Birincil birlikte çalışma Derlemeleriyle programlama](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/baxfadst(v=vs.100))
- [Birincil birlikte çalışma derlemelerini bulma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/y06sxw56(v=vs.100))
- [Birincil birlikte çalışma derlemelerini yeniden dağıtma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w0dt2w20(v=vs.100))
