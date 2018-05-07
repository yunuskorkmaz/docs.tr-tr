---
title: F# Kılavuzu
description: 'Bu kılavuz çeşitli öğrenim malzemelerini F #, .NET çalıştıran işlevsel bir programlama dili için genel bir bakış sağlar.'
author: jackfoxy
ms.date: 03/19/2018
ms.openlocfilehash: 393214a5da7445d8ee3dced844da8592f4ca6d31
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="f-guide"></a>F# Kılavuzu

F # .NET üzerinde çalışan bir işlevsel programlama dilidir. Ayrıca karışım işlevsel ve herhangi bir sorun için kolay çözümleri için nesne programlama izin vererek nesneleri için tam destek içerir.

```fsharp
open System // Get access to functionality in System namespace.

// Function: takes a name and produces a greeting.
let getGreeting name =
    sprintf "Hello, %s! Isn't F# great?" name

// Use the EntryPoint attribute to run the program.
[<EntryPoint>]
let main args =
    // Define a list of names
    let names = [| "Don"; "Julia"; "Xi" |]
    
    // Print a fun greeting for each name!
    names
    |> Array.map getGreeting
    |> Array.iter (fun greeting -> printfn "%s" greeting)

    0
```

F # kendi merkezinde üretkenlik hakkındadır. F # için araç desteği her yerden ve Gelişmiş özelliklerin tam ' dir.

## <a name="learning-f"></a>F # öğrenme #

[F # Turu](tour.md) kod örnekleri çok önemli dil özelliklerine genel bakış sağlar. F # için yeni ve dilinin nasıl çalıştığını için bir fikir almak istiyorsanız bu önerilir.

[F # Visual Studio ile çalışmaya başlama](get-started/get-started-visual-studio.md) Windows olduğunuz ve tam Visual Studio IDE (Integraded geliştirme ortamı) deneyimi istiyor.

[F # Visual Studio için Mac kullanmaya başlama](get-started/get-started-with-visual-studio-for-mac.md) üzerinde macOS olduğunuz ve Visual Studio IDE kullanmak istiyorsanız.

[F # Visual Studio Code ile çalışmaya başlama](get-started/get-started-vscode.md) hafif, platformlar arası istediğiniz ve özellik dolu IDE deneyimi.

[F # .NET Core CLI ile başlayın](get-started/get-started-command-line.md) komut satırı araçları kullanmak istiyorsanız.

[F # ve Xamarin kullanmaya başlama](https://docs.microsoft.com/xamarin/cross-platform/platform/fsharp/) mobil programlama ile F # için.

## <a name="references"></a>Referanslar

[F # dili başvurusu](language-reference/index.md) resmi, kapsamlı tüm F # dili özellikleri başvurudur. Her makalede söz dizimi açıklanmıştır ve kod örnekleri gösterilir. Belirli makaleleri bulmak için içindekiler tablosunda filtre çubuğunu kullanabilirsiniz.

[F # Core kitaplık başvurusu](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference) F # Core kitaplık için API Başvurusu değil.


## <a name="additional-guides"></a>Ek kılavuzları

[F # eğlenceli ve kar](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/) F # öğrenme üzerinde kapsamlı ve çok ayrıntılı bir kitap. F # topluluk tarafından vaftizine içeriklerini ve yazar. Hedef kitle öncelikle geliştiriciler nesne yönelimli programlama arka plana sahip olur.

[F # Wikibook programlama](https://en.wikibooks.org/wiki/F_Sharp_Programming) F # öğrenme hakkında bir wikibook değil. F # topluluk, bir ürün de olabilir. Hedef kitle yeni F #, biraz nesne yönelimli programlama arka plan ile birden çok kişi var.

## <a name="learn-f-through-videos"></a>F # videolar bilgi edinin

[F # Öğreticisi YouTube'da](https://www.youtube.com/watch?v=c7eNDJN758U) harika bir F Visual Studio kullanarak, çok sayıda harika örnekler 1,5 saat boyunca gösteren # giriş yapılır. Hedef kitle F # için yeni Visual Studio geliştiriciler ' dir.

[F # ile programlamaya giriş](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC) ana düzenleyicisi olarak Visual Studio Code kullanan harika bir video serisidir. Video serisi, herhangi bir şey başlar ve bir metin tabanlı RPG video oyun oluşturma ile biter. Hedef kitle geliştiriciler Visual Studio Code'da (veya basit bir IDE) tercih ve F # için yeni ' dir.

[F # için geliştiriciler için Visual Studio 2017'de](https://www.linkedin.com/learning/what-s-new-in-visual-studio-2017-for-f-sharp-for-developers) yeni özelliklerden bazıları için F #'de Visual Studio 2017 gösteren bir video yol kullanmamaktır. Hedef kitle F # için yeni Visual Studio geliştiriciler ' dir.

## <a name="other-useful-resources"></a>Diğer kullanışlı kaynaklar

[F # kod parçacıkları Web sitesi](http://www.fssnip.net) nasıl F mutlak başlangıç için yüksek oranda Gelişmiş parçacıkları arasında değişen #, neredeyse her şeyi yapılacağını gösteren kod parçacıkları yoğun bir kümesini içerir.

[F # yazılım Foundation kayma](http://fsharp.org/guides/slack/) yeni başlayanlar ve uzmanlar aynı şekilde, yüksek oranda active için harika bir yerdir ve dünyanın en iyi F # programcıları için Sohbet kullanılabilir bazıları vardır. Birleştirme öneririz.

## <a name="the-f-software-foundation"></a>F # yazılım Foundation

Microsoft, Visual Studio Araçları ile F # dili ve birincil geliştirici olsa da, F # Ayrıca, F # yazılım Foundation (FSSF) gibi bağımsız bir foundation tarafından desteklenir.

F # yazılım Foundation Görev yükseltmek, korumak ve F # programlama dilini ilerletmek için destek ve F # programcıları farklı ve uluslararası topluluğu büyümesini kolaylaştırmak sağlamaktır.

Daha fazla bilgi edinin ve söz konusu almak için kullanıma [fsharp.org](http://fsharp.org). Katılmak ücretsizdir ve F # geliştiricileri Foundation'da ağ kaçırılması out için istemediğiniz bir şeydir!
