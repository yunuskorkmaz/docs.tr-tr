---
ms.openlocfilehash: e7d35045892c62f759aad5067962ac5c15a9fb8b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602931"
---

Hem .NET Core SDK hem de .NET Core çalışma zamanı, indirildikten sonra el ile yüklenebilir. .NET Core SDK yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez. İlk olarak, aşağıdaki sitelerden birinden SDK veya çalışma zamanı için ikili bir sürüm indirin:

- ✔️ [.net 5,0 Preview İndirmeleri](https://dotnet.microsoft.com/download/dotnet/5.0)
- ✔️ [.NET Core 3,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- ❌[.NET Core 3,0 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- ❌[.NET Core 2,2 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- ✔️ [.NET Core 2,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/2.1)

Ardından, indirilen dosyayı ayıklayın ve `export` .NET Core tarafından kullanılan değişkenleri ayarlamak için komutunu kullanın ve ardından .NET Core 'un yolunda olduğundan emin olun.

Çalışma zamanını ayıklamak ve .NET Core CLI komutlarının terminalde kullanılabilir hale getirmek için önce bir .NET Core ikili sürümü indirin. Ardından, bir Terminal açın ve dosyanın kaydedildiği dizinden aşağıdaki komutları çalıştırın.

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> Yukarıdaki `export` Komutlar yalnızca .NET Core CLI komutlarını çalıştırıldığı terminal oturumu için kullanılabilir hale getirir.
>
> Komutları kalıcı olarak eklemek için kabuk profilinizi düzenleyebilirsiniz. Linux için kullanılabilen birçok farklı kabuk vardır ve her birinin farklı bir profili vardır. Örnek:
>
> - **Bash kabuğu**: *~/. bash_profile*, *~/,bashrc*
> - **Korn kabuğu**: *~/,KSHRC* veya *. Profile*
> - **Z kabuğu**: *~/,zshrc* veya *. zprofile*
>
> Kabuğunuz için uygun kaynak dosyayı düzenleyin ve `:$HOME/dotnet` var olan deyimin sonuna ekleyin `PATH` . Hiçbir `PATH` ifade dahil yoksa, ile yeni bir satır ekleyin `export PATH=$PATH:$HOME/dotnet` .
>
> Ayrıca, `export DOTNET_ROOT=$HOME/dotnet` dosyanın sonuna ekleyin.

Bu yaklaşım ayrı konumlara farklı sürümler yüklemenize ve hangi uygulamayı kullanmak üzere açık bir şekilde tercih etmenize olanak tanır.
