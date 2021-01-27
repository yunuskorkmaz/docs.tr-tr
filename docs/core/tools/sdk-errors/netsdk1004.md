---
title: 'NETSDK1004: varlıklar dosyası bulunamadı'
description: project.assets.jsdosya bulunamadığında oluşan .NET SDK hatası NETSDK1004 hakkında bilgi edinin.
ms.topic: error-reference
ms.date: 01/26/2021
f1_keywords:
- NETSDK1004
ms.openlocfilehash: ed42ad0e8ebef7362cc029125fe51d3f300acbae
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98900362"
---
# <a name="netsdk1004-assets-file-not-found"></a>NETSDK1004: varlıklar dosyası bulunamadı

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2.1.100 SDK ve sonraki sürümleri

Bu hata, derleme sırasında *project.assets.js* varlıklar dosyası bulunamadığında oluşur. Tam hata iletisi şuna benzerdir:

**NETSDK1004: ' C:\IncorrectPath\project.assets.json ' varlık dosyası bulunamadı. Bu dosyayı oluşturmak için bir NuGet paketi geri yükleme çalıştırın.**

`dotnet build`Komutu bir karakter içeren bir dizin yolundan çalıştırırsanız, uyarı NETSDK1004 ile karşılaşabilirsiniz `%` .
