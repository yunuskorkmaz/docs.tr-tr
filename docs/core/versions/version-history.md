---
title: Sürüm oluşturma .NET Core SDK'sını nasıl değiştirildi
description: Bu makalede nasıl çalışma zamanı ve .NET Core SDK'sı sürüm v2.1 zaman çerçevesinde değiştirilmiş açıklanır.
ms.date: 07/26/2018
ms.custom: seodec18
ms.openlocfilehash: e4b87d2ebd6dc5a0d5b874dc35dcaf746fdd4a0a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53131137"
---
# <a name="net-core-version-changes-between-10-and-21"></a>NET Core 1.0 ve 2.1 arasındaki sürüm değişiklikleri

.NET Core SDK ve .NET Core çalışma zamanı üzerinde farklı temposu sürüm olduğundan, .NET Core için sürüm numaraları zor. Farklı temposu, yalnızca iki aşağıdaki üç şeyi yapmak için takım zorlandı anlamına gelir:

1. Yayın bağımsız olarak, özellikle araçları, C# ve VB .NET Core çalışma zamanı daha hızlı ilerlemek için izin verme.
2. .NET Core SDK ve .NET Core çalışma zamanı arasındaki sürüm numaralarında hizalama korur.
3. Semantic versioning .NET Core SDK ve .NET Core çalışma zamanı için kullanın.

2.0.0 sürümü hizalama zorlamalı ve sorunsuz bir sürüm için proceeded. Aralık 2017'de .NET Core SDK'sı, .NET Core çalışma zamanı içinde ilgili hiçbir sürümüne sahip bir özellik yayını vardı. Takım hedeflerine 1 ve 3, SDK ve .NET Core çalışma zamanı arasında hizalama kaybetme seçtiniz. Birkaç .NET Core SDK'sı 2.1.x sürümü, .NET Core çalışma zamanı 2.1 önce kullanıma sunulmuştur. SDK'sı ileten uyumlu olmadığından, bu 2.1.x SDK sürümleri .NET Core çalışma zamanı 2.1 hedefleyebileceği değil. Takım hedeflerine 1 ve 2 ' nin semantic versioning açıklandığı gibi bırakıp geçerek önemli ölçüde karışıklığa yanıt [.NET Core sürüm](index.md#versioning-details).

Semantic versioning bırakmaya karar zamanlama nedeniyle, ayrıca .NET Core çalışma zamanı 2.1 hedefleyemezsiniz 2.1.10x ve 2.1.20x sürüm numarası aralıklarını geçiş sürümlerde vardı.

İlk iki basamak sürüm numaralarının ile 2.1.0 oranında düşürülecektir. .NET Core çalışma zamanı ve 2.1.300 sürümünü .NET Core SDK sürümü.

Çerçeve ve dilden derleyici sürümleri dahil olmak üzere ayrı ayrı bileşenler sürümleri hakkında ayrıntılı bilgi bulunabilir [.NET Core indirmeler sayfasına](https://www.microsoft.com/net/download/dotnet-core/current). Önceki sürümleri hakkında ayrıntılı bilgi için istenen sürümden seçin [.NET Core indirme sayfası arşivleri](https://www.microsoft.com/net/download/archives). Ayrıntılı destek bilgileri açıklayan resmi makalesinde bulunabilir [.NET desteği İlkesi](https://www.microsoft.com/net/Support/Policy).