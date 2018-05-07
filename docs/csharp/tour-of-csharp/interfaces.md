---
title: C# arabirimleri - C# dili turu
description: C# türleri tarafından uygulanan sözleşmeler arabirim tanımlar
ms.date: 08/10/2016
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: 0ad02d5b2792656783d93b2cc767aeb81efbc30e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="interfaces"></a>Arabirimler

Bir ***arabirimi*** sınıflar ve yapılar tarafından uygulanan bir sözleşme tanımlar. Arabirim yöntemleri, özellikleri, olayları ve dizin oluşturucular içerebilir. Arabirim uygulamaları tanımladığı üyelerinin sağlamaz — yalnızca bir sınıf ya da arabirimini uygulayan yapının tarafından sağlanmalıdır üyeleri belirtir.

Arabirimleri uygulamadığınız ***birden çok devralma***. Aşağıdaki örnekte, arabirim `IComboBox` hem de devralır `ITextBox` ve `IListBox`.

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

Sınıflar ve yapılar birden çok arabirimi uygulayabilirsiniz. Aşağıdaki örnekte, sınıf `EditBox` her ikisi de uygulayan `IControl` ve `IDataBound`.

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

Sınıfta veya yapı belirli bir arabirimi uygulayan, o sınıfta veya yapı örnekleri, arabirim türüne örtük olarak dönüştürülebilir. Örneğin

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

Dinamik tür atamaları burada örneği statik olarak belirli bir arabirim uygulamak için bilinmiyor durumlarda kullanılabilir. Örneğin, bir nesnenin elde etmek için dinamik tür atamaları aşağıdaki deyimleri kullanın `IControl` ve `IDataBound` arabirimi uygulamaları. Nesne çalışma zamanı gerçek tür olduğundan `EditBox`, atamaları başarılı.

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

Önceki `EditBox` sınıfı, `Paint` yönteminden `IControl` arabirimi ve `Bind` yönteminden `IDataBound` arabirimi Genel üyeler kullanılarak uygulanır. C# de destekler açık ***arabirim üye uygulamaları***, sınıf veya Yapı üyeleri ortak yapmaktan kaçınmak için etkinleştirme. Açık arabirim üye uygulaması tam arabirimi üye adı kullanılarak yazılır. Örneğin, `EditBox` sınıf uygulama `IControl.Paint` ve `IDataBound.Bind` yöntemlerini açık kullanarak arabirimi üye uygulamaları gibi.

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

Açık arabirim üyeleri yalnızca arabirim türü erişilebilir. Örneğin, uyarlamasını `IControl.Paint` tarafından önceki EditBox sınıfı yalnızca ilk dönüştürerek çağrılabilir sağlanan `EditBox` başvuru `IControl` arabirim türü.

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
[Önceki](arrays.md)
[sonraki](enums.md)
