---
title: 'NETSDK1064: paket bulunamadı'
description: Bir paket bulunamadığında oluşan .NET SDK hatası NETSDK1064 hakkında bilgi edinin.
ms.topic: error-reference
ms.date: 02/10/2021
f1_keywords:
- NETSDK1064
ms.openlocfilehash: 1a155db1aacbceb9878401dbcac61ece5f1f9824
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488337"
---
# <a name="netsdk1064-package-not-found"></a>NETSDK1064: paket bulunamadı

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2.1.100 SDK ve sonraki sürümleri

Bu hata, derleme araçları proje oluşturmak için gereken bir NuGet paketini bulamadığında oluşur. Bunun nedeni genellikle bir paket geri yükleme sorunudur. Tam hata iletisi aşağıdaki örneğe benzer:

> NETSDK1064: ' PackageName ' paketi, sürüm x. x. x bulunamadı. NuGet geri yüklemeden bu yana silinmiş olabilir. Aksi takdirde, NuGet geri yükleme yalnızca kısmen tamamlanmış olabilir. Bu, en fazla yol uzunluğu kısıtlamalarından kaynaklanabilir.

Bu hatayı çözmek için gerçekleştirebileceğiniz bazı eylemler şunlardır:

* `/restore` *MSBuild.exe* Komutunuz için seçeneğini ekleyin. `/t:Restore;Build`, Bu, hafif hatalara yol açacak şekilde kullanmayın. Bir alternatif `dotnet build` , otomatik olarak bir paket geri yüklemesi yaptığından, komutunu kullanmaktır.
* Visual Studio 2019 veya *MSBuild.exe* kullanarak paket geri yükleme çalıştırıyorsanız, hata en büyük yol uzunluğu kısıtlamalarına neden olabilir. Daha fazla bilgi için bkz. [uzun yol desteği (NUGET CLI)](/nuget/reference/cli-reference/cli-ref-long-path) ve [NuGet/ev sorunu #3324](https://github.com/NuGet/Home/issues/3324).
* X86 *nuget.exe* geri yüklüyorsanız ve x64 *MSBuild.exe* ile derleme yapıyorsanız, eşleşmeyen bit durumu bu hataya neden olabilir. Derleme, geri yükleme taleplerinin elde ettiği paketleri bulamıyor, çünkü *project.assets.js* içindeki yol, farklı bir bitme işleminde çalışmıyor. Hatayı gidermek için, geri yükleme ve derleme için aynı bit durumuyla araçları kullanın veya paketleri x86 ve x64 arasında sanallaştırmayı desteklemeyen bir klasöre geri yüklemek için NuGet 'i yapılandırın. Daha fazla bilgi için bkz. [DotNet/Core sorun #4332](https://github.com/dotnet/core/issues/4332).
* Docker görüntüsü oluşturuyorsanız, *. dockerıgnore* dosyasının *bin* ve *obj* dizinlerini yoksaymasını sağlayın. Daha fazla bilgi için bkz. [NETSDK1064: Package DnsClient, 1.2.0 bulunamadı](https://stackoverflow.com/questions/61167032/error-netsdk1064-package-dnsclient-1-2-0-was-not-found).
