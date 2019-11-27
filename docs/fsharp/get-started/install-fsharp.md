---
title: F# yükleme
description: Ortamınıza göre yüklemeyi F# öğrenin.
ms.date: 09/05/2019
ms.openlocfilehash: 592a4c7763266cee68809fca84f9604d7e96b8f1
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204867"
---
# <a name="install-f"></a>F\# 'yi yükler

Ortamınıza bağlı olarak F# birden çok şekilde yükleyebilirsiniz.

## <a name="install-f-with-visual-studio"></a>Visual F# Studio ile Install

[Visual Studio 'yu](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) ilk kez indiriyorsanız, Ilk olarak Visual Studio yükleyicisi 'ni yükler. Yükleyiciden uygun Visual Studio SKU 'sunu yükleme. Zaten yüklüyse **Değiştir**' e tıklayın.

Daha sonra Iş yüklerinin bir listesini görürsünüz. ASP.NET Core projelerine yönelik destek ve .NET Core desteğini F# yükleyecek **ASP.net ve Web geliştirme '** yi seçin.

Sonra sağ alt taraftaki **Değiştir** ' e tıklayın.  Bu işlem, seçtiğiniz her şeyi yükler. Ardından Başlat ' a tıklayarak Visual Studio 2017 F# ' i dil desteğiyleaçabilirsiniz.

## <a name="install-f-with-visual-studio-code"></a>Visual Studio Code F# ile yüklensin

İlk olarak, git ' in [yüklü](https://git-scm.com/download) olduğundan ve yolunuzda kullanılabilir olduğundan emin olun. Bir komut isteminde `git --version` yazarak ve **ENTER**tuşuna basarak, doğru şekilde yüklendiğini doğrulayabilirsiniz.

Sonra, [.NET Core SDK](https://dotnet.microsoft.com/download)' yi yükler.

Daha sonra [Visual Studio Code](https://code.visualstudio.com) yüklenmesi gerekir.

Sonra, uzantılar simgesine tıklayın ve "ıonıde" araması yapın:

Visual Studio Code ' de destek için F# gereken tek eklenti [ıonıde-FSharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)' dir. Ancak, [paket](https://fsprojects.github.io/Paket/) desteğini almak için [sahte](https://fake.build/) destek ve [ıonıde-paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) sağlamak üzere [ıonıde-sahte](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) ' i de yükleyebilirsiniz. SAHTE ve paket, sırasıyla F# projeler oluşturmaya ve bağımlılıkları yönetmeye yönelik ek topluluk araçlarıdır.

## <a name="install-f-with-visual-studio-for-mac"></a>Mac için Visual Studio F# ile yüklensin

F#, seçtiğiniz yapılandırma bağımsız olarak [Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)varsayılan olarak yüklenir.

Yüklemesi tamamlandıktan sonra, "Visual Studio 'Yu Başlat" ı seçin. MacOS 'ta Finder aracılığıyla da başlatabilirsiniz.

## <a name="install-f-on-a-build-server"></a>Derleme F# sunucusuna yüklensin

.NET Core veya .NET SDK aracılığıyla .NET Framework kullanıyorsanız, derleme sunucunuza .NET SDK 'yı yüklemeniz yeterlidir. İhtiyacınız olan her şeye sahiptir.

.NET Framework kullanıyorsanız ve .NET **SDK kullanmıyorsanız,** [Visual Studio derleme araçları SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) 'sunu Windows sunucunuza yüklemeniz gerekecektir. Yükleyicide, **.net masaüstü derleme araçları** ' nı seçin ve ardından yükleyici menüsünün sağ tarafındaki  **F# derleyici** bileşenini seçin.
