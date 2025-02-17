---
title: 'NETSDK1004: varlıklar dosyası bulunamadı'
description: project.assets.jsdosya bulunamadığında oluşan .NET SDK hatası NETSDK1004 hakkında bilgi edinin.
ms.topic: error-reference
ms.date: 01/29/2021
f1_keywords:
- NETSDK1004
ms.openlocfilehash: aa01ff657143faac96baa5ae1133493516edfb1c
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102206719"
---
# <a name="netsdk1004-assets-file-not-found"></a>NETSDK1004: varlıklar dosyası bulunamadı

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2.1.100 SDK ve sonraki sürümleri

NuGet, *obj* klasöründe *project.assets.js* adlı bir dosya yazar ve .NET SDK bunu derleyiciye geçirilecek paketler hakkında bilgi almak için kullanır. Bu hata, derleme sırasında *project.assets.js* varlıklar dosyası bulunamadığında oluşur. Tam hata iletisi aşağıdaki örneğe benzer:

**NETSDK1004: ' C:\path\to\project.assets.json ' varlık dosyası bulunamadı. Bu dosyayı oluşturmak için bir NuGet paketi geri yükleme çalıştırın.**

Hatanın olası nedenleri şunlardır:

* `dotnet build`Komutunu bir karakter içeren bir dizin yolundan çalıştırıyorsunuz `%` . Hatayı gidermek için, `%` öğesini klasör adından kaldırın ve yeniden çalıştırın `dotnet build` .
* Proje dosyası değişikliği proje sistemi tarafından otomatik olarak algılanmadı ve geri yüklenemedi. Hatayı gidermek için bir komut istemi açın ve `dotnet restore` projede çalıştırın.
* Bir proje, Nuget.exe eski bir sürümü tarafından ayrı olarak geri yüklendi. Hatayı gidermek için bir komut istemi açın ve `dotnet restore` projede çalıştırın.
* NETSDK1045 (kullandığınız SDK sürümü projenin hedef çerçevesini desteklemez) gibi önceki bir hata, NuGet 'in proje varlıkları dosyasını oluşturmasını engelledi. NETSDK1004 hatasını çözümlemek için, önceki hatayı çözün ve sonra `dotnet restore` projede çalıştırın.
* App Center CI, NuGet içinde olmayan bir dış derlemeye sahip bir proje oluşturuyor. Hatayı gidermek için, derleme için bir NuGet paketi kullanın.
* Bir noktayla başlayan bir adla Visual Studio 'Ya bir çözüm klasörü eklediniz. Hatayı gidermek için, klasör adından önde gelen süreyi kaldırın.
