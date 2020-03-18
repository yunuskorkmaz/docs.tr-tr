---
title: C# Arayüzler - C# dilinde bir tur
description: "Arabirimler C'deki türlere göre uygulanan sözleşmeleri tanımlar #"
ms.date: 02/27/2020
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: 62d94462fa481379cf70d63a598deb7f36be204f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159136"
---
# <a name="interfaces"></a>Arabirimler

***Arabirim,*** sınıflar ve structs tarafından uygulanabilen bir sözleşme tanımlar. Arabirim yöntemleri, özellikleri, olayları ve dizinleyicileri içerebilir. Arabirim, tanımladığı üyelerin uygulamalarını sağlamaz, yalnızca arabirimi uygulayan sınıflar veya yapıstları tarafından sağlanmalıdır.

Arabirimler ***birden çok devralma***istihdam edebilir. Aşağıdaki örnekte, arabirim `IComboBox` her `ITextBox` ikisinden ve `IListBox`.

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

Sınıflar ve structs birden çok arabirim uygulayabilirsiniz. Aşağıdaki örnekte, sınıf `EditBox` hem `IControl` ve `IDataBound`.

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

Bir sınıf veya yapı belirli bir arabirimi uyguladığında, o sınıfın veya yapının örnekleri örtülü olarak bu arabirim türüne dönüştürülebilir. Örneğin:

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

Bir örneğin belirli bir arabirimi uygulamak için statik olarak bilinmediği durumlarda, dinamik tür dökümleri kullanılabilir. Örneğin, aşağıdaki ifadeler bir nesnenin `IControl` ve `IDataBound` arabirim uygulamalarını elde etmek için dinamik tür dökümleri kullanır. Nesnenin çalışma zamanı gerçek türü `EditBox`olduğundan, dökümler başarılı dır.

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

Önceki `EditBox` `Paint` sınıfta, `IControl` arabirimden gelen `Bind` yöntem ve `IDataBound` arabirimden gelen yöntem ortak üyeler kullanılarak uygulanır. C# ayrıca açık ***arabirim üyesi uygulamalarını***da destekler ve üyeleri herkese açık hale getirmemek için sınıfın veya yapının kullanılmasını sağlar. Açık bir arayüz üye uygulaması tam nitelikli arabirim üye adı kullanılarak yazılır. Örneğin, `EditBox` sınıf `IControl.Paint` ve `IDataBound.Bind` yöntemleri aşağıdaki gibi açık arabirim üye uygulamalarını kullanarak uygulayabilir.

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

Açık arabirim üyelerine yalnızca arabirim türünden erişilebilir. Örneğin, önceki EditBox sınıfı tarafından `IControl.Paint` sağlanan uygulama yalnızca ilk `EditBox` `IControl` olarak başvuruyu arabirim türüne dönüştürerek çağrılabilir.

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
>[Önceki](arrays.md)
>[Sonraki](delegates.md)
