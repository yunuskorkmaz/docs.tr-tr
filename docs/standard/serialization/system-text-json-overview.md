---
title: C#-.NET kullanarak JSON serisini serileştirme ve serisini kaldırma
description: Bu genel bakışta, System.Text.Json .net 'TEKI JSON 'a serileştirmek ve seri durumdan çıkarmak için ad alanı işlevselliği açıklanmaktadır.
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 909d979d46b30939e304af071de65d230febd92d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "83380131"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a>.NET 'te JSON serileştirme ve seri durumundan çıkarma (sıralama ve kaldırma)-genel bakış

`System.Text.Json`Ad alanı, JavaScript nesne gösterimi (JSON) öğesinden serileştirmek ve seri durumdan çıkarmak için işlevsellik sağlar.

Kitaplık tasarımı, kapsamlı bir özellik kümesi üzerinden yüksek performans ve düşük bellek ayırmayı vurgular. Yerleşik UTF-8 desteği, UTF-8 olarak kodlanmış JSON metnini okuma ve yazma sürecini en iyi duruma getirir. Bu, Web ve disk üzerindeki dosyalardaki veriler için en yaygın kodlama olur.

Kitaplık Ayrıca, bellek içi belge nesne modeli (DOM) ile çalışmak için sınıflar sağlar. Bu özellik bir JSON dosyası veya dizesindeki öğelerin rastgele salt okunurdur erişimine izin vermez.

## <a name="how-to-get-the-library"></a>Kitaplığı alma

* Kitaplığı, [.NET Core 3,0](https://aka.ms/netcore3download) paylaşılan çerçevesinin bir parçası olarak yerleşik olarak bulunur.
* Diğer hedef çerçeveler için [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet paketini yükler. Paket şunları destekler:
  * .NET Standard 2,0 ve sonraki sürümler
  * .NET Framework 4.7.2 ve sonraki sürümler
  * .NET Core 2,0, 2,1 ve 2,2

## <a name="additional-resources"></a>Ek kaynaklar

* [Kitaplığı kullanma](system-text-json-how-to.md)
* [Öğesinden geçişNewtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [Dönüştürücüler yazma](system-text-json-converters-how-to.md)
* [System.Text.Jsonkaynak kodu](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)
* [System.Text.JsonAPI başvurusu](xref:System.Text.Json)
* [System.Text.Json. Serileştirme API başvurusu](xref:System.Text.Json.Serialization)
<!-- * [Roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
