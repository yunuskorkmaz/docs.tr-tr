---
ms.openlocfilehash: ea2883912907843e4b6d65db5ba186af43f27aaa
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85805654"
---

<!-- Note, this content is copied in ../macos.md. Any fixes should be applied there too, though content may be different -->

Paket yöneticilerine alternatif olarak SDK ve çalışma zamanını indirip el ile yükleyebilirsiniz. El ile yüklemeyi genellikle sürekli tümleştirme testi kapsamında veya desteklenmeyen bir Linux dağıtımında gerçekleştirilir. Bir geliştirici veya Kullanıcı için genellikle bir paket yöneticisi kullanmak daha iyidir.

.NET Core SDK yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez. İlk olarak, aşağıdaki sitelerden birinden SDK veya çalışma zamanı için **ikili** bir sürüm indirin:

- ✔️ [.net 5,0 Preview İndirmeleri](https://dotnet.microsoft.com/download/dotnet/5.0)
- ✔️ [.NET Core 3,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- ✔️ [.NET Core 2,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [Tüm .NET Core İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core)

Ardından, indirilen dosyayı ayıklayın ve `export` .NET Core tarafından kullanılan değişkenleri ayarlamak için komutunu kullanın ve ardından .NET Core 'un yolunda olduğundan emin olun.

Çalışma zamanını ayıklamak ve .NET Core CLI komutlarının terminalde kullanılabilir hale getirmek için önce bir .NET Core ikili sürümü indirin. Ardından, bir Terminal açın ve dosyanın kaydedildiği dizinden aşağıdaki komutları çalıştırın. Arşiv dosyası adı, indirdiklerinize bağlı olarak farklı olabilir.

**Çalışma zamanını ayıklamak için aşağıdaki komutu kullanın**:

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

**SDK 'yı ayıklamak için aşağıdaki komutu kullanın**:

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-3.1.301-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> Yukarıdaki `export` Komutlar yalnızca .NET Core CLI komutlarını çalıştırıldığı terminal oturumu için kullanılabilir hale getirir.
>
> Komutları kalıcı olarak eklemek için kabuk profilinizi düzenleyebilirsiniz. Linux için kullanılabilen birçok farklı kabuk vardır ve her birinin farklı bir profili vardır. Örneğin:
>
> - **Bash kabuğu**: *~/. bash_profile*, *~/,bashrc*
> - **Korn kabuğu**: *~/,KSHRC* veya *. Profile*
> - **Z kabuğu**: *~/,zshrc* veya *. zprofile*
>
> Kabuğunuz için uygun kaynak dosyayı düzenleyin ve `:$HOME/dotnet` var olan deyimin sonuna ekleyin `PATH` . Hiçbir `PATH` ifade dahil yoksa, ile yeni bir satır ekleyin `export PATH=$PATH:$HOME/dotnet` .
>
> Ayrıca, `export DOTNET_ROOT=$HOME/dotnet` dosyanın sonuna ekleyin.

Bu yaklaşım ayrı konumlara farklı sürümler yüklemenize ve hangi uygulamayı kullanmak üzere açık bir şekilde tercih etmenize olanak tanır.
