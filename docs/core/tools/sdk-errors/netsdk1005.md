---
title: 'NETSDK1005 ve NETSDK1047: varlık dosyasında hedef yok'
description: Bir hedef eksik olan varlık dosyası sorununu çözme.
author: sfoslund
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1005
- NETSDK1047
ms.openlocfilehash: 6c22fd8c79c2ac6e024b46b4f67e08011d42efc6
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91957170"
---
# <a name="netsdk1005-and-netsdk1047-asset-file-is-missing-target"></a>NETSDK1005 ve NETSDK1047: varlık dosyasında hedef yok

**Bu makale şu şekilde geçerlidir:** ✔️ .NET 2.1.100 SDK ve sonraki sürümleri

.NET SDK hatası NETSDK1005 veya NETSDK1047 hata verdiği zaman, projenin varlıklar dosyasında hedef çerçevelerinizdeki bir bilgi eksik. Bu, genellikle geri yüklemenin çalıştırıldığından ve eksik hedef değerin projenizin özelliğine eklendiğinden emin olarak düzeltilebilir `TargetFrameworks` .

> [!NOTE]
> Bu hataya neden olan Visual Studio 16,8 önizlemeleri sürümleriyle kullanıldığında .NET 5 Preview 8 ' in erken Derlemeleriyle ilgili bilinen bir sorun oluştu. Özellikle, eksik hedef `net5.0-windows7.0` veya ise `net5.0` , Visual Studio 'nun en son sürümlerine ve .NET 5 SDK 'sına güncelleştirdiğinizden emin olun.
