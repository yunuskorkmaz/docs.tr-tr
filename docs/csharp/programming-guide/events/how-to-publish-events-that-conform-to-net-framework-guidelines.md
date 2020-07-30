---
title: .NET yönergeleriyle uyumlu olayları yayımlama-C# Programlama Kılavuzu
description: .NET yönergelerine uygun olan olayları yayımlamayı öğrenin. .NET Framework sınıf kitaplığındaki tüm olaylar EventHandler temsilcisini temel alır.
ms.date: 05/26/2020
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 1b802e236026911b55bafcb3f48d487c43bba174
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302119"
---
# <a name="how-to-publish-events-that-conform-to-net-guidelines-c-programming-guide"></a>.NET yönergeleriyle uyumlu olayları yayımlama (C# Programlama Kılavuzu)

Aşağıdaki yordamda, sınıflarınıza ve yapılarına standart .NET modelini izleyen olayların nasıl ekleneceği gösterilmektedir. .NET Framework sınıf kitaplığındaki tüm olaylar <xref:System.EventHandler> , aşağıdaki şekilde tanımlanan temsilciyi temel alır:

```csharp
public delegate void EventHandler(object sender, EventArgs e);
```

> [!NOTE]
> .NET Framework 2,0, bu temsilcinin genel bir sürümünü sunmaktadır <xref:System.EventHandler%601> . Aşağıdaki örneklerde her iki sürümün de nasıl kullanılacağı gösterilmektedir.

Tanımladığınız sınıflardaki olaylar geçerli temsilci türlerini temel alabilir, hatta bir değer döndüren temsilciler bile, <xref:System.EventHandler> Aşağıdaki örnekte gösterildiği gibi kullanarak olaylarınızı .net düzenine dayandırırsınız.

Bu ad, `EventHandler` olayı gerçekten işlemediği için bir karışıklığına neden olabilir. <xref:System.EventHandler>, Ve genel <xref:System.EventHandler%601> temsilci türleridir. İmza, temsilci tanımıyla eşleşen bir yöntem veya lambda ifadesi *olay işleyicisidir* ve olay harekete çıktığında çağrılacaktır.

## <a name="publish-events-based-on-the-eventhandler-pattern"></a>Etkinlik, EventHandler düzenine göre yayımlayın

1. (Bu adımı atlayın ve olaylarınız ile özel veriler göndermeniz gerekmez. adıma gidin.) Özel verilerinize ait sınıfı, hem Yayımcı hem de abone sınıflarınızda görünen bir kapsamda bildirin. Ardından, özel olay verilerinizi tutmak için gerekli üyeleri ekleyin. Bu örnekte basit bir dize döndürülür.

    ```csharp
    public class CustomEventArgs : EventArgs
    {
        public CustomEventArgs(string message)
        {
            Message = message;
        }

        public string Message { get; set; }
    }
    ```

2. (Genel sürümünü kullanıyorsanız bu adımı atlayın <xref:System.EventHandler%601> .) Yayımlama sınıfınıza bir temsilci bildirin. İle biten bir ad verin `EventHandler` . İkinci parametre özel `EventArgs` türünü belirtir.

    ```csharp
    public delegate void CustomEventHandler(object sender, CustomEventArgs args);
    ```

3. Aşağıdaki adımlardan birini kullanarak, yayımlama sınıfınıza olayı bildirin.

    1. Özel EventArgs sınıfınız yoksa, olay türü genel olmayan EventHandler temsilcisi olur. <xref:System>C# projenizi oluştururken dahil edilen ad alanında zaten bildirildiği için temsilciyi bildirmeniz gerekmez. Aşağıdaki kodu Publisher sınıfınıza ekleyin.

        ```csharp
        public event EventHandler RaiseCustomEvent;
        ```

    2. Öğesinin genel olmayan sürümünü kullanıyorsanız <xref:System.EventHandler> ve öğesinden türetilmiş özel bir sınıfınız varsa, bu kodunuzu <xref:System.EventArgs> Yayımlama sınıfınız içinde bildirin ve 2. adımdaki temsilcinizi tür olarak kullanın.

        ```csharp
        public event CustomEventHandler RaiseCustomEvent;
        ```

    3. Genel sürümü kullanıyorsanız özel bir temsilciye ihtiyacınız yoktur. Bunun yerine, yayımlama sınıfınız içinde, `EventHandler<CustomEventArgs>` kendi sınıfınızın adını açılı ayraçlar arasında değiştirerek olay türü olarak belirtirsiniz.

        ```csharp
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;
        ```

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir özel EventArgs sınıfı ve olay türü olarak önceki adımları gösterir <xref:System.EventHandler%601> .

[!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Delegate>
- [C# Programlama Kılavuzu](../index.md)
- [Ekinlikler](index.md)
- [Temsilciler](../delegates/index.md)
