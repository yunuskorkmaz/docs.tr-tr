---
title: C# geliştiricileri için sürüm ve güncelleştirme konuları
description: Kitaplığınızda yeni dil özellikleri ile tanışın, bunu kullanan kod etkileyebilir.
ms.date: 09/19/2018
ms.openlocfilehash: 3ffe2f6fd64a391fddf28233dccb022c95851884
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634485"
---
# <a name="version-and-update-considerations-for-c-developers"></a>C# geliştiricileri için sürüm ve güncelleştirme konuları

C# dili için yeni özellikler eklendikçe uyumluluk çok önemli bir hedeftir. Hemen hemen tüm durumlarda, herhangi bir sorun olmadan yeni bir derleyici sürümü ile mevcut kodu yeniden derlenmesi.

Yeni dil özellikleri bir kitaplıkta benimsediğinizde, daha fazla dikkat gerekli olabilir. Yeni bir kitaplık en yeni sürümünde bulunan özellikler ile oluşturduğunuz ve derleyicinin önceki sürümleri kullanılarak oluşturulan uygulamaları sağlamak için kullanabilmesi. Veya varolan bir kitaplığını yükseltme ve kullanıcılarınızın çoğu sürümler henüz yükseltilmemiş. Yeni özellikler benimseme hakkında kararlar gibi uyumluluk iki çeşidi göz önünde bulundurmanız gerekir: kaynak uyumlu ve uyumlu ikili.

## <a name="binary-compatible-changes"></a>İkili uyumlu değişiklikleri

Değişiklikler kitaplığınıza **uyumlu ikili** zaman güncelleştirilmiş kitaplığınızı kullanılabilir uygulamaları ve kitaplıkları kullanan derlenmeden. Bağımlı derlemelerin yeniden oluşturulması için gerekli değildir ve herhangi bir kaynak kod değişikliği gereklidir. İkili uyumlu değişiklikleri de kaynak uyumlu değişikliklerdir.

## <a name="source-compatible-changes"></a>Kaynak uyumlu değişiklikleri

Değişiklikler kitaplığınıza **kaynak uyumlu** zaman uygulamaları ve kitaplıkları, kitaplığı kullanan kaynak kod değişikliği gerektirmez, ancak kaynak düzgün çalışması için yeni sürümü karşı derlenmesi gerekiyor.

## <a name="incompatible-changes"></a>Uyumsuz değişiklikleri

Bir değişiklik ne ise **kaynak uyumlu** ya da **uyumlu ikili**, bağımlı kitaplıkları ve uygulamaları kaynak kodu değişiklikleri birlikte yeniden derleme gereklidir.

## <a name="evaluate-your-library"></a>Kitaplığınızı değerlendir

Bu uyumluluk kavramları için kendi iç uygulama kitaplığınızın ortak ve korunan bildirimleri etkiler. Herhangi bir yeni özellik dahili olarak kullandığı her zaman **uyumlu ikili**.  

**İkili uyumlu** değişiklikleri genel bildirimleri eski sözdizimi olarak aynı derlenmiş kodunu üretir yeni söz dizimi sağlar. Örneğin, bir ifade gövdeli üyesine bir yöntemi değiştirme olduğu bir **uyumlu ikili** değiştirin:

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

**Kaynak uyumlu** değişikliğine neden söz dizimi genel bir üyenin, ancak mevcut çağrı siteleri bir şekilde uyumlu olarak derlenmiş kodunu değiştirir. Örneğin, bir yöntem imzasının değiştirilmesi bir değer parametresi tarafından bir `in` başvuruya göre kaynak uyumlu parametredir, ancak ikili uyumlu:

Özgün kod:

```csharp
public double CalculateSquare(double value) => value * value;
```

Yeni kod:

```csharp
public double CalculateSquare(in double value) => value * value;
```

[Yenilikler](index.md) makaleleri ortak bildirimleri etkileyen bir özellik ile tanışın kaynak uyumlu ya da ikili uyumlu olup olmadığını unutmayın.
