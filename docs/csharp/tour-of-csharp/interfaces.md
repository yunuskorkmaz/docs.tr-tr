---
title: C#Arabirimleri - Turu C# dil
description: Sözleşmeler türleri tarafından uygulanan arabirimler tanımlarC#
ms.date: 08/10/2016
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: bfc6b59a411ff2ddb3331a8bdf24c0ae3d611273
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706409"
---
# <a name="interfaces"></a>Arabirimler

Bir ***arabirimi*** sınıfları ve yapıları tarafından uygulanan bir sözleşmeyi tanımlar. Bir arabirim yöntemleri, özellikleri, olayları ve dizin oluşturucular içerebilir. Bir arabirim tanımlar üyelerinin uygulamalarını sağlamaz; yalnızca bir sınıf ya da arabirimi uygulayan yapının tarafından sağlanması gereken üyeleri belirtir.

, Arabirimleri görevlendirmek ***birden çok devralma***. Aşağıdaki örnekte, arabirim `IComboBox` hem de devralan `ITextBox` ve `IListBox`.

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

Sınıflar ve yapı birimleri birden fazla arabirim uygulayabilir. Aşağıdaki örnekte, sınıf `EditBox` hem `IControl` ve `IDataBound`.

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

Bir sınıf veya yapı, belirli bir arabirim uygular, bu sınıfın veya yapının örneği, bir arabirim türüne örtük olarak dönüştürülebilir. Örneğin:

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

Dinamik tür atamaları, burada bir örnek statik olarak belirli bir arabirim uygulamak için bilinmiyor durumlarda kullanılabilir. Örneğin, bir nesnenin elde etmek için dinamik tür atamaları aşağıdaki deyimleri kullanın `IControl` ve `IDataBound` arabirimi uygulamaları. Nesnenin çalışma zamanı gerçek türü olduğundan `EditBox`, yayınları başarılı.

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

Önceki `EditBox` sınıfı `Paint` yönteminden `IControl` arabirimi ve `Bind` yönteminden `IDataBound` arabirimi Genel üyeler kullanılarak uygulanır. C#aynı zamanda açık destekler ***arabirim üyesi uygulamaları***, sınıfın veya yapının üyeleri genel yapmaktan kaçınmak için etkinleştiriliyor. Açık arabirim üyesi uygulaması, tam bir arabirim üye adını kullanarak yazılır. Örneğin, `EditBox` sınıf uygulama `IControl.Paint` ve `IDataBound.Bind` yöntemlerini kullanarak açık arabirim üyesi uygulamaları gibi.

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

Açık arabirim üyeleri yalnızca arabirim türü erişilebilir. Örneğin, uygulanması `IControl.Paint` tarafından önceki EditBox sınıfı yalnızca ilk dönüştürerek çağrılabilir sağlanan `EditBox` başvurusu `IControl` arabirim türü.

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
>[Önceki](arrays.md)
>[İleri](enums.md)