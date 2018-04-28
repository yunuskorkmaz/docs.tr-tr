---
title: 'Yapılandırma projelerini (F #)'
description: 'F # Visual Studio projelerinde ile çalışırken, Proje Tasarımcısı kullanmayı öğrenin.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: eac5b61d6b61d2aa1cb7b1606d60995a0355e975
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="configuring-projects-in-visual-studio"></a>Visual Studio projeleri yapılandırma

> [!NOTE]
Bu makale, en son Visual Studio ile güncel değil.  Güncelleştirilecek.

Bu konu nasıl kullanılacağı hakkında bilgi içerir **Proje Tasarımcısı** F # projeleri ile çalışırken. F # projeleri ile çalışma Visual Basic veya C# projeleri ile çalışmaktan önemli ölçüde farklı değildir. F # kullandığınızda, genel Visual Studio Proje belgelerini genellikle birincil başvuru olarak kullanabilirsiniz. Bu konu, diğer Visual Studio dilleri ile paylaşılan ayarları için Visual Studio belgesinde ilgili bilgilere bağlantılar sağlar ve ayrıca F # için özel ayarları açıklanır.

## <a name="project-designer"></a>Proje Tasarımcısı
**Proje Tasarımcısı** ve genel kullanımı tam konu başlığı altında açıklanan [Proje Tasarımcısı giriş](https://msdn.microsoft.com/library/898dd854-c98d-430c-ba1b-a913ce3c73d7) Visual Studio belgelerinde. **Proje Tasarımcısı** ilgili işlevsellik tarafından gruplandırılmış birçok sayfadan oluşur. F # projeleri için kullanılabilir sayfaları çoğunlukla bu diğer diller için kullanılabilir bir alt kümesidir. F #'de desteklenen sayfaları aşağıdaki tabloda açıklanmıştır. F #'de kullanılabilir olmayan veya bir komut satırı seçeneği yalnızca değiştirerek kullanılabilir olan özellikler için kullanılabilir değil sayfaları ilgilidir. Bir bağlantı ilgili C# sağlanır şekilde F #'da kullanılabilir sayfalar C# sayfalarına en yakından benzer **Proje Tasarımcısı** sayfası.

|Proje Tasarımcısı sayfası|İlgili bağlantılar|Açıklama|
|---------------------|-------------|-----------|
|`Application`|[Uygulama sayfası, Proje Tasarımcısı &#40;C&#35;&#41;](https://msdn.microsoft.com/library/ms247046.aspx)|Uygulama düzeyi ayarlarını ve bir kitaplık veya yürütülebilir bir dosyanın, .NET Framework'ün hangi sürümünün uygulama hedefleme ve burada kaynak dosyaları hakkında bilgi oluşturmakta olduğunuz gibi özelliklerini belirtmenize olanak tanıyan uygulama kullandığı depolanır.|
|`Build`|[Derleme sayfası, Proje Tasarımcısı &#40;C&#35;&#41;](https://msdn.microsoft.com/library/kb4wyys2.aspx)|Kodun nasıl derlendiğini denetlemenizi sağlar.|
|`Build Events`|[Derleme olayları sayfası, Proje Tasarımcısı &#40;C&#35;&#41;](https://msdn.microsoft.com/library/kb4wyys2.aspx)|Önce veya sonra bir derleme çalıştırılacak komutları belirtmenizi sağlar.|
|`Debug`|[Hata Ayıklama Sayfası, Proje Tasarımcısı](https://msdn.microsoft.com/library/2wcdezs5.aspx)|Uygulama hata ayıklama sırasında nasıl çalışacağını denetlemenizi sağlar. Bu içerdikleri komut satırını kullanacağınızı ve uygulamanızın başlangıç dizini nedir ve herhangi bir özel hata ayıklama modunu yerel kod ve SQL gibi etkinleştirmek istediğiniz.|
|`Reference Paths`|[Bir projedeki başvuruları yönetme](/visualstudio/ide/managing-references-in-a-project)|Kodu bağımlı derlemeler için arama yeri belirtmenizi sağlar.|

## <a name="f-specific-settings"></a>F #-belirli ayarları
F # için belirli ayarları aşağıdaki tabloda özetlenmiştir:

|Proje Tasarımcısı sayfası|Ayar|Açıklama|
|---------------------|-------|-----------|
|`Build`|`Generate tail calls`|Seçili olduğunda, Microsoft Ara dili (MSIL) yönerge tail kullanımını etkinleştirir. Bu kuyruk özyinelemeli işlevler için yeniden yığın çerçevesi neden olur. Eşdeğer `--tailcalls` derleyici seçeneği.|
|`Build`|`Other flags`|Ek derleyici komut satırı seçeneklerini belirtmenizi sağlar.|

## <a name="see-also"></a>Ayrıca Bkz.
 [F # Visual Studio ile çalışmaya başlama](../get-started/get-started-visual-studio.md)  
 [Derleyici Seçenekleri](../language-reference/compiler-options.md)  
 [Proje Tasarımcısı giriş](https://msdn.microsoft.com/library/898dd854-c98d-430c-ba1b-a913ce3c73d7(v=vs.100))
