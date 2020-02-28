---
title: C#Arabirimler- C# dilin turu
description: İçindeki türler tarafından uygulanan sözleşmeleri tanımlayan arabirimlerC#
ms.date: 02/27/2020
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: 62d94462fa481379cf70d63a598deb7f36be204f
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159136"
---
# <a name="interfaces"></a>Arabirimler

***Arabirim*** , sınıflar ve yapılar tarafından uygulanabilecek bir sözleşmeyi tanımlar. Arabirim, Yöntemler, özellikler, olaylar ve Dizin oluşturucular içerebilir. Arabirim, tanımladığı üyelerin uygulamalarını sağlamaz; yalnızca arabirimini uygulayan sınıflar veya yapılar tarafından sağlanması gereken üyeleri belirtir.

Arabirimler ***birden fazla devralma***kullanabilir. Aşağıdaki örnekte, arabirimi `IComboBox` `ITextBox` ve `IListBox`devralır.

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

Sınıflar ve yapılar birden çok arabirim uygulayabilir. Aşağıdaki örnekte, sınıfı `EditBox` hem `IControl` hem de `IDataBound`uygular.

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

Bir sınıf veya yapı belirli bir arabirimi uygularsa, bu sınıfın veya yapının örnekleri örtülü olarak bu arabirim türüne dönüştürülebilir. Örneğin:

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

Bir örneğin belirli bir arabirimi uygulamak için statik olarak bilinen bir durum olduğu durumlarda, dinamik tür atamaları kullanılabilir. Örneğin, aşağıdaki deyimler bir nesnenin `IControl` ve `IDataBound` arabirim uygulamalarını almak için dinamik tür yayınları kullanır. Nesnenin çalışma zamanı gerçek türü `EditBox`olduğundan, yayınlar başarılı olur.

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

Önceki `EditBox` sınıfında, `IControl` arabiriminden `Paint` yöntemi ve `IDataBound` arabirimindeki `Bind` yöntemi ortak Üyeler kullanılarak uygulanır. C#Ayrıca, açık ***arabirim üye uygulamalarını***destekler, bu sayede, üyeleri genel hale getirmeyi önlemek için sınıfı veya yapıyı etkinleştirir. Açık arabirim üyesi uygulama, tam nitelikli arabirim üye adı kullanılarak yazılır. Örneğin `EditBox` sınıfı, aşağıdaki gibi açık arabirim üye uygulamalarını kullanarak `IControl.Paint` ve `IDataBound.Bind` yöntemlerini uygulayabilir.

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

Açık arabirim üyelerine yalnızca arabirim türü aracılığıyla erişilebilir. Örneğin, önceki EditBox sınıfı tarafından sunulan `IControl.Paint` uygulanması yalnızca `IControl` arabirimi türüne `EditBox` başvurusu dönüştürülürken çağrılabilir.

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
>[Önceki](arrays.md)
>[İleri](delegates.md)
