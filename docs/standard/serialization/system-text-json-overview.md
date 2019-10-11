---
title: .NET kullanarak C# JSON serisini serileştirme ve serisini kaldırma
author: tdykstra
ms.author: tdykstra
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: 5ce98a7908470a402779436db43333d46f5101fc
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72180151"
---
# <a name="json-serialization-in-net---overview"></a>.NET 'te JSON serileştirme-genel bakış

@No__t-0 ad alanı, JavaScript Nesne Gösterimi (JSON) ' den serileştirmek ve seri durumdan çıkarmak için işlevsellik sağlar.

Kitaplık tasarımı, kapsamlı bir özellik kümesi üzerinden yüksek performans ve düşük bellek ayırmayı vurgular. Yerleşik UTF-8 desteği, UTF-8 olarak kodlanmış JSON metnini okuma ve yazma sürecini en iyi duruma getirir. Bu, Web ve disk üzerindeki dosyalardaki veriler için en yaygın kodlama olur.

Kitaplık Ayrıca, bellek içi belge nesne modeli (DOM) ile çalışmak için sınıflar sağlar. Bu özellik bir JSON dosyası veya dizesindeki öğelerin rastgele salt okunurdur erişimine izin vermez. 

## <a name="how-to-get-the-library"></a>Kitaplığı alma

* Kitaplığı, [.NET Core 3,0](https://aka.ms/netcore3download) paylaşılan çerçevesinin bir parçası olarak yerleşik olarak bulunur.
* Diğer hedef çerçeveler için [System. Text. JSON](https://www.nuget.org/packages/System.Text.Json) NuGet paketini yükler. Paket şunları destekler:
  * .NET Standard 2,0 ve sonraki sürümler
  * .NET Framework 4.6.1 ve sonraki sürümler
  * .NET Core 2,0, 2,1 ve 2,2

## <a name="additional-resources"></a>Ek kaynaklar

* [Kitaplığı kullanma](system-text-json-how-to.md)
* [Kaynak kod](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json)
* [API başvurusu](xref:System.Text.Json)
* [Yol Haritası](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/roadmap/README.md)
* DotNet/corefx deposundaki GitHub sorunları
  * [System. Text. JSON geliştirmesi hakkında tartışma](https://github.com/dotnet/corefx/issues/33115)
  * [Tüm System. Text. JSON sorunları](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)
  * [JSON işlevi etiketli System. Text. JSON sorunları-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc)
