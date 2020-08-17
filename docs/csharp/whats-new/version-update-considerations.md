---
title: C# geliştiricileri için sürüm ve güncelleştirme konuları
description: Kitaplığınızdaki yeni dil özelliklerine giriş, onu kullanan kodu etkileyebilir.
ms.topic: reference
ms.date: 09/19/2018
ms.openlocfilehash: f7db7c79792d04bcf592bc1858e1f0f05cb34402
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88268133"
---
# <a name="version-and-update-considerations-for-c-developers"></a>C# geliştiricileri için sürüm ve güncelleştirme konuları

Yeni özellikler C# diline eklendikçe uyumluluk çok önemli bir hedeftir. Neredeyse tüm durumlarda, mevcut kod herhangi bir sorun olmadan yeni bir derleyici sürümü ile yeniden derlenir.

Yeni dil özelliklerini bir kitaplıkta benimsediğinizde daha dikkatli olmanız gerekebilir. En son sürümde bulunan özelliklerle yeni bir kitaplık oluşturabilir ve derleyicinin önceki sürümlerini kullanarak oluşturulan uygulamaların bunu kullanmasını sağlayabilirsiniz. Ya da var olan bir kitaplığı yükseltiyor olabilirsiniz ve kullanıcılarınızın birçoğu henüz yükseltilmiş sürüme sahip olmayabilir. Yeni özellikleri benimseme konusunda kararlar verirken, iki uyumluluk çeşitlemelerini göz önünde bulundurmanız gerekir: kaynak ile uyumlu ve ikili uyumlu.

## <a name="binary-compatible-changes"></a>İkili uyumlu değişiklikler

Güncelleştirilmiş kitaplığınız, onu kullanan uygulamaları ve kitaplıkları yeniden oluşturmadan kullanılabilir olduğunda, kitaplığınızdaki değişiklikler **ikili uyumludur** . Bağımlı derlemelerin yeniden oluşturulması gerekmez, ya da herhangi bir kaynak kod değişikliği gerekli değildir. İkili uyumlu değişiklikler de kaynak ile uyumlu değişikliklerdir.

## <a name="source-compatible-changes"></a>Kaynak ile uyumlu değişiklikler

Kitaplığınızda yapılan değişiklikler, kitaplığınızı kullanan uygulamalar ve kitaplıklar kaynak kodu değişiklikleri gerektirmiyorsa kaynak **uyumludur** , ancak kaynağın doğru çalışması için yeni sürüme yeniden derlenmesi gerekir.

## <a name="incompatible-changes"></a>Uyumsuz değişiklikler

Bir değişiklik, **kaynak uyumlu** veya **ikili uyumlu**değilse, bağımlı kitaplıklar ve uygulamalarda yeniden derleme ile birlikte kaynak kodu değişiklikleri gerekir.

## <a name="evaluate-your-library"></a>Kitaplığınızı değerlendirin

Bu uyumluluk kavramları, kendi iç uygulamasına değil, kitaplığınız için ortak ve korumalı bildirimleri etkiler. Yeni özellikleri dahili olarak benimseme her zaman **ikili uyumludur**.  

**İkili uyumlu** değişiklikler, eski sözdizimi olarak genel bildirimler için aynı derlenmiş kodu oluşturan yeni bir sözdizimi sağlar. Örneğin, bir yöntemi ifade olarak değiştirmek-Bodied üyesi, **ikili uyumlu** bir değişiklik olur:

Özgün kod:

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

**Kaynak ile uyumlu** değişiklikler ortak üye için derlenen kodu değiştiren, ancak mevcut çağrı siteleriyle uyumlu bir şekilde bir sözdizimi sunar. Örneğin, bir by değeri parametresindeki bir yöntem imzasını bir `in` başvuru parametresine değiştirmek, kaynak uyumludur, ancak ikili uyumlu değildir:

Özgün kod:

```csharp
public double CalculateSquare(double value) => value * value;
```

Yeni kod:

```csharp
public double CalculateSquare(in double value) => value * value;
```

Genel bildirimleri etkileyen bir özelliğin tanıtımı, kaynak ile uyumlu veya ikili uyumlu olduğunu gösteren [Yeni](index.md) makalelerdir.
