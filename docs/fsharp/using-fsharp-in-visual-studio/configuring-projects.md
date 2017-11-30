---
title: "Yapılandırma projelerini (F #)"
description: "F # Visual Studio projelerinde ile çalışırken, Proje Tasarımcısı kullanmayı öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8b2ed206-34e4-4256-a6ce-0c2499561165
ms.openlocfilehash: d2a92f725c40443c8dc6af593d28deccd3ee88de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="configuring-projects-in-visual-studio"></a>Visual Studio projeleri yapılandırma

> [!NOTE]
Bu makale, en son Visual Studio ile güncel değil.  Güncelleştirilecek.

Bu konu nasıl kullanılacağı hakkında bilgi içerir **Proje Tasarımcısı** F # projeleri ile çalışırken. F # projeleri ile çalışma Visual Basic veya C# projeleri ile çalışmaktan önemli ölçüde farklı değildir. F # kullandığınızda, genel Visual Studio Proje belgelerini genellikle birincil başvuru olarak kullanabilirsiniz. Bu konu, diğer Visual Studio dilleri ile paylaşılan ayarları için Visual Studio belgesinde ilgili bilgilere bağlantılar sağlar ve ayrıca F # için özel ayarları açıklanır.

## <a name="project-designer"></a>Proje Tasarımcısı
**Proje Tasarımcısı** ve genel kullanımı tam konu başlığı altında açıklanan [Proje Tasarımcısı giriş](https://msdn.microsoft.com/library/898dd854-c98d-430c-ba1b-a913ce3c73d7) Visual Studio belgelerinde. **Proje Tasarımcısı** ilgili işlevsellik tarafından gruplandırılmış birçok sayfadan oluşur. F # projeleri için kullanılabilir sayfaları çoğunlukla bu diğer diller için kullanılabilir bir alt kümesidir. F #'de desteklenen sayfaları aşağıdaki tabloda açıklanmıştır. F #'de kullanılabilir olmayan veya bir komut satırı seçeneği yalnızca değiştirerek kullanılabilir olan özellikler için kullanılabilir değil sayfaları ilgilidir. Bir bağlantı ilgili C# sağlanır şekilde F #'da kullanılabilir sayfalar C# sayfalarına en yakından benzer **Proje Tasarımcısı** sayfası.

|Proje Tasarımcısı sayfası|İlgili bağlantılar|Açıklama|
|---------------------|-------------|-----------|
|`Application`|[Uygulama sayfası, Proje Tasarımcısı &#40; C &#35; &#41;](https://msdn.microsoft.com/library/ms247046.aspx)|Uygulama düzeyi ayarlarını ve bir kitaplık veya yürütülebilir bir dosyanın, .NET Framework'ün hangi sürümünün uygulama hedefleme ve burada kaynak dosyaları hakkında bilgi oluşturmakta olduğunuz gibi özelliklerini belirtmenize olanak tanıyan uygulama kullandığı depolanır.|
|`Build`|[Derleme sayfası, Proje Tasarımcısı &#40; C &#35; &#41;](https://msdn.microsoft.com/library/kb4wyys2.aspx)|Kodun nasıl derlendiğini denetlemenizi sağlar.|
|`Build Events`|[Derleme olayları sayfası, Proje Tasarımcısı &#40; C &#35; &#41;](https://msdn.microsoft.com/library/kb4wyys2.aspx)|Önce veya sonra bir derleme çalıştırılacak komutları belirtmenizi sağlar.|
|`Debug`|[Hata ayıklama sayfası, Proje Tasarımcısı](https://msdn.microsoft.com/library/2wcdezs5.aspx)|Uygulama hata ayıklama sırasında nasıl çalışacağını denetlemenizi sağlar. Bu içerdikleri komut satırını kullanacağınızı ve uygulamanızın başlangıç dizini nedir ve herhangi bir özel hata ayıklama modunu yerel kod ve SQL gibi etkinleştirmek istediğiniz.|
|`Reference Paths`|[Bir projedeki başvuruları yönetme](https://msdn.microsoft.com/library/ez524kew.aspx)|Kodu bağımlı derlemeler için arama yeri belirtmenizi sağlar.|

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
