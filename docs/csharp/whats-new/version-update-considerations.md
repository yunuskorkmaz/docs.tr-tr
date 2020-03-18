---
title: C# geliştiricileri için sürüm ve güncelleştirme konuları
description: Kitaplığınızda yeni dil özelliklerinin tanıtılması, onu kullanan kodu etkileyebilir.
ms.date: 09/19/2018
ms.openlocfilehash: 3ffe2f6fd64a391fddf28233dccb022c95851884
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399387"
---
# <a name="version-and-update-considerations-for-c-developers"></a>C# geliştiricileri için sürüm ve güncelleştirme konuları

C# diline yeni özellikler eklendikçe uyumluluk çok önemli bir hedeftir. Hemen hemen her durumda, varolan kod herhangi bir sorun olmadan yeni bir derleyici sürümü ile yeniden derlenebilir.

Kitaplıkta yeni dil özelliklerini benimsediğinizde daha fazla özen gerektirebilir. En son sürümde bulunan özelliklere sahip yeni bir kitaplık oluşturuyor olabilirsiniz ve derleyicinin önceki sürümlerini kullanarak oluşturulmuş uygulamaların bu kitaplığı kullanabileceğinden emin olmanız gerekir. Veya varolan bir kitaplığı yükseltiyor olabilirsiniz ve kullanıcılarınızın çoğu henüz sürümlerini yükseltmemiş olabilir. Yeni özellikleri benimseme konusunda karar vererken, iki uyumluluk varyasyonu göz önünde bulundurmanız gerekir: kaynak uyumluluğu ve ikili uyumlu.

## <a name="binary-compatible-changes"></a>İkili uyumlu değişiklikler

Güncelleştirilmiş kitaplığınız, onu kullanan uygulamaları ve kitaplıkları yeniden oluşturmadan kullanılabildiğinde kitaplığınızdaki değişiklikler **ikili uyumludur.** Bağımlı derlemelerin yeniden oluşturulması gerekmez veya kaynak kodu değişiklikleri gerekmez. İkili uyumlu değişiklikler de kaynak uyumlu değişikliklerdir.

## <a name="source-compatible-changes"></a>Kaynak uyumlu değişiklikler

Kitaplığınızı kullanan uygulamalar ve kitaplıklar kaynak kodu değişiklikleri gerektirmediğinde, kaynağın doğru çalışması için yeni sürüme karşı yeniden derlenmiş olması gerekirken kitaplığınızdaki değişiklikler **kaynak uyumludur.**

## <a name="incompatible-changes"></a>Uyumsuz değişiklikler

Bir değişiklik ne **kaynak uyumlu** ne de ikili **uyumlu**ise, bağımlı kitaplıklarda ve uygulamalarda yeniden derleme ile birlikte kaynak kodu değişiklikleri gereklidir.

## <a name="evaluate-your-library"></a>Kitaplığınızı değerlendirin

Bu uyumluluk kavramları, iç uygulamasını değil, kitaplığınız için genel ve korumalı bildirimleri etkiler. Herhangi bir yeni özelliği n içini dahili olarak benimsemek her zaman **ikili uyumludur.**  

**İkili uyumlu** değişiklikler, eski sözdizimi yle aynı derlenmiş genel bildirimler için derlenmiş kodu oluşturan yeni sözdizimi sağlar. Örneğin, bir yöntemi ifade gövdeli bir üyeye değiştirmek **ikili uyumlu** bir değişikliktir:

Orijinal kod:

```csharp
public double CalculateSquare(double value)
{
    return value * value;
}
```

Yeni kod:

```csharp
public double CalculateSquare(double value) => value * value;
```

**Kaynak uyumlu** değişiklikler, derlenen bir üye için derlenen kodu, ancak varolan arama siteleriyle uyumlu bir şekilde değiştiren sözdizimini sunar. Örneğin, bir yöntem imzasını bir değer parametresi ile referans parametreye `in` değiştirmek kaynak uyumludur, ancak ikili uyumlu değildir:

Orijinal kod:

```csharp
public double CalculateSquare(double value) => value * value;
```

Yeni kod:

```csharp
public double CalculateSquare(in double value) => value * value;
```

Ortak bildirimleri etkileyen bir özellik tanıtılması kaynak uyumlu veya ikili uyumlu [ise, yeni](index.md) makaleler ne notu.
