---
title: F# yükleme
description: F#'yi farklı şekillerde nasıl yükleyin öğrenin.
ms.date: 12/20/2019
ms.openlocfilehash: 302e04f7cf3271516dff88d9d5f18f620b6ede80
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400248"
---
# <a name="install-f"></a>F Yükle\#

Ortamınıza bağlı olarak F#'yi birden çok şekilde yükleyebilirsiniz.

## <a name="install-f-with-visual-studio"></a>Visual Studio ile F# yükle

1. [Visual Studio'yu](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ilk kez indiriyorsanız, ilk olarak Visual Studio Installer'ı yükler. Yükleyiciden Visual Studio'nun uygun sürümünü yükleyin.

   Visual Studio zaten yüklüyse, F# eklemek istediğiniz sürümün yanında **Değiştir'i** seçin.

2. İş Yükleri sayfasında, ASP.NET Core projeleri için F# ve .NET Core desteğini içeren **ASP.NET ve web geliştirme** iş yükünü seçin.

3. Seçtiğiniz her şeyi yüklemek için sağ alt köşede **Değiştir'i** seçin.

   Daha sonra Visual Studio Installer **başlat'ı** seçerek F# ile Visual Studio'u açabilirsiniz.

## <a name="install-f-with-visual-studio-code"></a>Visual Studio Code ile F# yükle

1. [Git'in](https://git-scm.com/download) path'inizde yüklü ve kullanılabilir olduğundan emin olun. Komut istemine girerek `git --version` ve **Enter**tuşuna basarak doğru yüklenmiş olduğunu doğrulayabilirsiniz.

2. [.NET Core SDK](https://dotnet.microsoft.com/download) ve [Visual Studio Kodunu](https://code.visualstudio.com)yükleyin.

3. Uzantılar simgesini seçin ve "Ionide" araması yapın:

   Visual Studio Code'da F# desteği için gerekli olan tek eklenti [Ionide-fsharp'dır.](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) Ancak, PAKET [desteği](https://fsprojects.github.io/Paket/) almak için [FAKE](https://fake.build/) desteği ve [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) almak için [ionide-FAKE'yi](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) de yükleyebilirsiniz. FAKE ve Paket, sırasıyla proje oluşturma ve bağımlılıkları yönetmek için ek F# topluluk araçlarıdır.

## <a name="install-f-with-visual-studio-for-mac"></a>Mac için Visual Studio ile F# yükleyin

F# varsayılan olarak [Mac için Visual Studio'da](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), hangi yapılandırmayı seçerseniz seçin yüklüdür.

Yükleme tamamlandıktan sonra **Görsel Stüdyoyu Başlat'ı**seçin. Visual Studio'u macOS'ta Finder aracılığıyla da açabilirsiniz.

## <a name="install-f-on-a-build-server"></a>Yapı sunucusuna F# yükleme

.NET SDK üzerinden .NET Core veya .NET Framework kullanıyorsanız, yapı sunucunuza .NET SDK'yı yüklemeniz yeterlidir. İhtiyacın olan her şey var.

.NET Framework kullanıyorsanız ve .NET SDK kullanmıyorsanız, [Visual Studio Build Tools SKU'yu](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) Windows Server'ınıza yüklemeniz gerekir. **not** Yükleyicide **.NET masaüstü oluşturma araçlarını**seçin ve ardından yükleyici menüsünün sağ tarafındaki **F# derleyici** bileşenini seçin.
