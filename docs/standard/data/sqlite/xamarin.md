---
title: Xamarin sınırlamaları
ms.date: 12/13/2019
description: Xamarin kullanırken karşılaştığınız kısıtlamaların bazılarını açıklar.
ms.openlocfilehash: 192f25954726919dc66d706e755e0853404b4d85
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447169"
---
# <a name="xamarin-limitations"></a>Xamarin sınırlamaları

Microsoft. Data. SQLite, 2,0 .NET Standard hedefler ve Xamarin 'te desteklenir. Aşağıdaki tabloda, varsayılan SQLitePCLRaw paketinin, için yerel SQLite ikililerini sağladığı platformlar gösterilmektedir. Farklı bir paket kullanma veya kendi yerel SQLite ikililerini sağlama hakkındaki ayrıntılar için bkz. [özel SQLite sürümleri](custom-versions.md) .

| Platform | SQLite ikililer |
| --- | --- |
| **Xamarin.Android** | — |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm64-v8a` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`armeabi-v7a` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86_64` | ✔ |
| **Xamarin.iOS** | ✔ |
| **Xamarin.Mac** | ✔ |
| **Xamarin. TVOS** | ✔ |
| **UWP** | — |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm64` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`x64` | ✔ |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86` | ✔ |

## <a name="ios"></a>iOS

Microsoft. Data. SQLite, SQLitePCLRaw paketlerini otomatik olarak başlatmaya çalışır. Ne yazık ki, Xamarin. iOS için sonraki zaman (AOT) derlemesinde sınırlamalar nedeniyle, deneme başarısız olur ve aşağıdaki hatayı alırsınız.

> Çağırmanız `SQLitePCL.raw.SetProvider()`gerekiyor. Paket paketi kullanıyorsanız, bu, çağırarak `SQLitePCL.Batteries.Init()`yapılır.

Paketi başlatmak için, Microsoft. Data. SQLite kullanılmadan önce aşağıdaki kod satırını uygulamanıza ekleyin.

```csharp
SQLitePCL.Batteries_V2.Init();
```

## <a name="see-also"></a>Ayrıca bkz.

* [Zaman uyumsuz sınırlamalar](async.md)
* [Özel SQLite sürümleri](custom-versions.md)
