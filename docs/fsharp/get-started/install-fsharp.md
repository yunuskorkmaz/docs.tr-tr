---
title: F# yükleme
description: Farklı yollarla nasıl yükleneceğini F# öğrenin.
ms.date: 12/20/2019
ms.openlocfilehash: 302e04f7cf3271516dff88d9d5f18f620b6ede80
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346562"
---
# <a name="install-f"></a>F\# 'yi yükler

Ortamınıza bağlı olarak F# birden çok şekilde yükleyebilirsiniz.

## <a name="install-f-with-visual-studio"></a>Visual F# Studio ile Install

1. [Visual Studio 'yu](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ilk kez indiriyorsanız, önce Visual Studio yükleyicisi yüklenir. Yükleyiciden uygun Visual Studio sürümünü yükleyin.

   Zaten Visual Studio yüklüyse, eklemek F# istediğiniz sürümün yanındaki **Değiştir** ' i seçin.

2. Iş yükleri sayfasında, ASP.NET Core projelerine yönelik ve .NET Core desteği içeren F# **ASP.net ve Web geliştirme** iş yükünü seçin.

3. Seçtiğiniz her şeyi yüklemek için sağ alt köşedeki **Değiştir** ' i seçin.

   Ardından Visual Studio Yükleyicisi 'de **Başlat** ' ı seçerek F# Visual Studio 'yu kullanabilirsiniz.

## <a name="install-f-with-visual-studio-code"></a>Visual Studio Code F# ile yüklensin

1. [Git](https://git-scm.com/download) ' in yüklü olduğundan ve yolunuzda kullanılabilir olduğundan emin olun. Bir komut istemine `git --version` girerek ve **ENTER**tuşuna basarak doğru şekilde yüklendiğini doğrulayabilirsiniz.

2. [.NET Core SDK](https://dotnet.microsoft.com/download) ve [Visual Studio Code](https://code.visualstudio.com)yükler.

3. Uzantılar simgesini seçin ve "ıonıde" araması yapın:

   Visual Studio Code ' de destek için F# gereken tek eklenti [ıonıde-FSharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)' dir. Ancak, [paket](https://fsprojects.github.io/Paket/) desteğini almak için [sahte](https://fake.build/) destek ve [ıonıde-paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) sağlamak üzere [ıonıde-sahte](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) ' i de yükleyebilirsiniz. SAHTE ve paket, sırasıyla F# projeler oluşturmaya ve bağımlılıkları yönetmeye yönelik ek topluluk araçlarıdır.

## <a name="install-f-with-visual-studio-for-mac"></a>Mac için Visual Studio F# ile yüklensin

F#, seçtiğiniz yapılandırma bağımsız olarak [Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)varsayılan olarak yüklenir.

Yüklemesi tamamlandıktan sonra **Visual Studio 'Yu Başlat**' ı seçin. Ayrıca, macOS 'ta Finder aracılığıyla Visual Studio 'Yu açabilirsiniz.

## <a name="install-f-on-a-build-server"></a>Derleme F# sunucusuna yüklensin

.NET Core veya .NET SDK aracılığıyla .NET Framework kullanıyorsanız, derleme sunucunuza .NET SDK 'yı yüklemeniz yeterlidir. İhtiyacınız olan her şeye sahiptir.

.NET Framework kullanıyorsanız ve .NET **SDK kullanmıyorsanız,** [Visual Studio derleme araçları SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) 'sunu Windows Server 'a yüklemeniz gerekir. Yükleyicide, **.net masaüstü derleme araçları**' nı seçin ve ardından yükleyici menüsünün sağ tarafındaki  **F# derleyici** bileşenini seçin.
