---
title: 'Nasıl yapılır: .NET Framework yönergeleri- C# programlama kılavuzuna uygun olan olayları yayımlayın'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 93924638fabe9a46af39006130d4f07de2ad0541
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590486"
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a>Nasıl yapılır: .NET Framework yönergelerine uygun olan olayları yayımlama (C# Programlama Kılavuzu)
Aşağıdaki yordam, sınıflarınıza ve yapılarına standart .NET Framework modelini izleyen olayların nasıl ekleneceğini göstermektedir. .NET Framework sınıf kitaplığındaki tüm olaylar, aşağıdaki şekilde tanımlanan <xref:System.EventHandler> temsilciyi temel alır:  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
>  .NET Framework 2,0, bu temsilcinin <xref:System.EventHandler%601>genel bir sürümünü sunmaktadır. Aşağıdaki örneklerde her iki sürümün de nasıl kullanılacağı gösterilmektedir.  
  
 Tanımladığınız sınıflardaki olaylar geçerli temsilci türlerini temel alabilir, hatta bir değer döndüren temsilciler olsa da, aşağıdaki örnekte gösterildiği gibi, kullanarak <xref:System.EventHandler>olaylarınızın .NET Framework düzeniyle temel almanız önerilir.  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a>Olayları EventHandler düzenine göre yayımlamak için  
  
1. (Bu adımı atlayın ve olaylarınız ile özel veriler göndermeniz gerekmez. adıma gidin.) Özel verilerinize ait sınıfı, hem Yayımcı hem de abone sınıflarınızda görünen bir kapsamda bildirin. Ardından, özel olay verilerinizi tutmak için gerekli üyeleri ekleyin. Bu örnekte basit bir dize döndürülür.  
  
    ```csharp  
    public class CustomEventArgs : EventArgs  
    {  
        public CustomEventArgs(string s)  
        {  
            msg = s;  
        }  
        private string msg;  
        public string Message  
        {  
            get { return msg; }  
        }   
    }  
    ```  
  
2. (Genel sürümünü <xref:System.EventHandler%601> kullanıyorsanız bu adımı atlayın.) Yayımlama sınıfınıza bir temsilci bildirin. Buna *EventHandler*ile biten bir ad verin. İkinci parametre özel EventArgs türünü belirtir.  
  
    ```csharp  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3. Aşağıdaki adımlardan birini kullanarak, yayımlama sınıfınıza olayı bildirin.  
  
    1. Özel EventArgs sınıfınız yoksa, olay türü genel olmayan EventHandler temsilcisi olur. Projenizi oluştururken dahil edilen <xref:System> ad alanında zaten bildirildiği için temsilciyi bildirmeniz gerekmez. C# Aşağıdaki kodu Publisher sınıfınıza ekleyin.  
  
        ```csharp  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2. Öğesinin <xref:System.EventHandler> genel olmayan sürümünü kullanıyorsanız ve öğesinden <xref:System.EventArgs>türetilmiş özel bir sınıfınız varsa, bu kodunuzu yayımlama sınıfınız içinde bildirin ve 2. adımdaki temsilcinizi tür olarak kullanın.  
  
        ```csharp  
        public event CustomEventHandler RaiseCustomEvent;  
        ```  
  
    3. Genel sürümü kullanıyorsanız özel bir temsilciye ihtiyacınız yoktur. Bunun yerine, yayımlama sınıfınız içinde, kendi sınıfınızın adını açılı ayraçlar arasında `EventHandler<CustomEventArgs>`değiştirerek olay türü olarak belirtirsiniz.  
  
        ```csharp  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir özel EventArgs sınıfı ve <xref:System.EventHandler%601> olay türü olarak önceki adımları gösterir.  
  
 [!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Delegate>
- [C# Programlama Kılavuzu](../index.md)
- [Olaylar](./index.md)
- [Temsilciler](../delegates/index.md)
