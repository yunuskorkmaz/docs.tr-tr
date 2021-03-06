---
title: "Son değişiklik: .NET Core yerine FrameworkDescription 'un değeri .NET"
description: RunTimeInformation. FrameworkDescription 'un şimdi ".NET Core" yerine ".NET" döndüğü çekirdek .NET kitaplıklarında .NET 5 ' in son değişikliği hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: 18aa9a30a149b3c38d4bbfe4a0c99446f4372f07
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257524"
---
# <a name="frameworkdescriptions-value-is-net-instead-of-net-core"></a>FrameworkDescription 'un değeri .NET Core yerine .NET

<xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> Şimdi ".NET Core" yerine ".NET" döndürür.

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> Açıklama dizesinin parçası olarak ".NET Core" döndürür. Örneğin, `.NET Core 3.1.1` .

.NET 5 ' den başlayarak, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> Açıklama dizesinin parçası olarak ".net" döndürür. Örneğin, `.NET 5.0.0` .

## <a name="reason-for-change"></a>Değişiklik nedeni

.NET 5 ile, `netcoreapp` `net` kısa hedef çerçeve bilinen adıyla değiştirilmiştir. Tutarlılık için çerçevenin açıklaması da güncelleştirilmiştir. Değişiklik, `FrameworkName` özelliğin dışında herhangi bir yerde kodlanmadığından, yüzeysel <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> .

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="recommended-action"></a>Önerilen eylem

Tarafından döndürülen dizedeki ".NET Core" için arama yapan tüm kodları güncelleştirin <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription> .

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
