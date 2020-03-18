---
title: .NET Framework Yönergelerine Uygun Etkinlikler Nasıl Yayımlanır - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 90c079b9f7dbf2a1d963b7eee4447145d7a10432
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167547"
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a>.NET Framework Yönergelerine Uygun Etkinlikler (C# Programlama Kılavuzu) nasıl yayımlanır?
Aşağıdaki yordam, sınıflarınıza ve yapılarınıza standart .NET Framework deseni izleyen olayların nasıl ekleyeceğinigösterir. .NET Framework sınıf kitaplığındaki tüm <xref:System.EventHandler> olaylar aşağıdaki gibi tanımlanan temsilciyi temel alar:  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
> .NET Framework 2.0 bu temsilcinin genel <xref:System.EventHandler%601>bir sürümünü sunar. Aşağıdaki örnekler, her iki sürümün nasıl kullanılacağını gösterir.  
  
 Tanımladığınız sınıflardaki olaylar herhangi bir geçerli temsilci türüne, hatta bir değer döndüren delegelere dayanabilir, ancak aşağıdaki <xref:System.EventHandler>örnekte gösterildiği gibi ,.'ı kullanarak olaylarınızı .NET Framework desenine dayandırdığınız önerilir.  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a>EventHandler deseni dayalı olayları yayımlamak için  
  
1. (Etkinliğinizle özel veri göndermeniz yoksa bu adımı atlayın ve Adım 3a'ya gidin.) Özel verileriniz için sınıfı hem yayımcınız hem de abone sınıflarınız tarafından görülebilecek bir kapsamda bildirin. Ardından, özel etkinlik verilerinizi tutmak için gerekli üyeleri ekleyin. Bu örnekte, basit bir dize döndürülür.  
  
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
  
2. (Genel sürümünü kullanıyorsanız bu adımı <xref:System.EventHandler%601> atlayın.) Yayımlama sınıfınızda bir temsilci bildirin. *EventHandler*ile biten bir ad verin. İkinci parametre özel EventArgs türünü belirtir.  
  
    ```csharp  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3. Aşağıdaki adımlardan birini kullanarak yayımlama sınıfınızdaki olayı bildirin.  
  
    1. Özel EventArgs sınıfınız yoksa, Etkinlik türünüz genel olmayan EventHandler temsilcisi olur. C# projenizi oluştururken dahil edilen <xref:System> ad alanında zaten beyan edildiğinden temsilciyi bildirmeniz gerekmez. Yayımcı sınıfınıza aşağıdaki kodu ekleyin.  
  
        ```csharp  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2. Genel olmayan sürümünü kullanıyorsanız <xref:System.EventHandler> ve türetilmiş özel bir <xref:System.EventArgs>sınıfınız varsa, yayımlama sınıfınızın içinde etkinliğinizi bildirin ve 2.  
  
        ```csharp  
        public event CustomEventHandler RaiseCustomEvent;  
        ```  
  
    3. Genel sürümü kullanıyorsanız, özel bir temsilciye ihtiyacınız yoktur. Bunun yerine, yayımlama sınıfınızda, olay `EventHandler<CustomEventArgs>`türünü açı ayraçları arasında kendi sınıfınızın adını yerine " olarak belirtirsiniz.  
  
        ```csharp  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, özel bir EventArgs sınıfı kullanarak <xref:System.EventHandler%601> ve olay türü olarak önceki adımları gösterir.  
  
 [!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Delegate>
- [C# Programlama Kılavuzu](../index.md)
- [Olaylar](./index.md)
- [Temsilciler](../delegates/index.md)
