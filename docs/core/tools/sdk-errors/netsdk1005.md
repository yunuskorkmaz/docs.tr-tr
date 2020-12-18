---
title: 'NETSDK1005 ve NETSDK1047: varlık dosyasında hedef yok'
description: Bir hedef eksik olan varlık dosyası sorununu çözme.
author: sfoslund
ms.topic: error-reference
ms.date: 12/17/2020
f1_keywords:
- NETSDK1005
- NETSDK1047
ms.openlocfilehash: e3e7389adf6a9a715d44661a5f7cbae5efe299e4
ms.sourcegitcommit: 4b79862c5b41fbd86cf38f926f6a49516059f6f2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/18/2020
ms.locfileid: "97678171"
---
# <a name="netsdk1005-and-netsdk1047-asset-file-is-missing-target"></a>NETSDK1005 ve NETSDK1047: varlık dosyasında hedef yok

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2.1.100 SDK ve sonraki sürümleri

.NET SDK hatası NETSDK1005 veya NETSDK1047 hata verdiği zaman, projenin varlıklar dosyasında hedef çerçevelerinizdeki bir bilgi eksik. NuGet, *obj* klasöründe *project.assets.js* adlı bir dosya yazar ve .NET SDK bunu derleyiciye geçirilecek paketler hakkında bilgi almak için kullanır. .NET 5 ' te, NuGet adlı yeni bir alan ekledi `TargetFrameworkAlias` , bu nedenle MSBuild veya NuGet 'in önceki sürümleri yeni alan olmadan bir varlık dosyası oluşturur. Daha fazla bilgi için bkz. [Error NETSDK1005](https://developercommunity.visualstudio.com/content/problem/1248649/error-netsdk1005-assets-file-projectassetsjson-doe.html).

Bu hatayı çözebilecek bazı eylemler şunlardır:

* MSBuild sürüm 16,8 veya üstünü, NuGet sürüm 5,8 veya üstünü kullandığınızdan emin olun ve araçlarınızı güncelleştirdikten sonra projeyi geri yükleyin. NuGet sürüm 5,8 veya üstünü kullanırken, Visual Studio 2019 sürüm 16,8 veya üzeri, MSBuild sürüm 16,8 veya üzeri ve .NET 5,0 SDK veya sonraki bir sürümünü kullanmanız gerekir.

* Visual Studio 2019 ' de proje derlerken hata alırsanız, sürüm 16,8 ' yi yükledikten sonra veya projenin hedef çerçevesini değiştirdikten sonra projeyi ikinci kez derleyin.

* Projeyi oluşturmadan önce *obj* klasörünü silin.

* Eksik hedef değerin projenizin özelliğine eklendiğinden emin olun `TargetFrameworks` .
