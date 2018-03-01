---
title: "Nasıl yapılır: .NET Framework Yönergeleriyle Uyumlu Olayları Yayımlama (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 570729e432146b4ef97e4c487f644b12b354bb4a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a>Nasıl yapılır: .NET Framework Yönergeleriyle Uyumlu Olayları Yayımlama (C# Programlama Kılavuzu)
Aşağıdaki yordam standarda olayları ekleneceği gösterilmektedir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sınıflar ve yapılar deseni. Tüm olaylar [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sınıf kitaplığı temel <xref:System.EventHandler> temsilci, hangi şu şekilde tanımlanır:  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
>  [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] Bu temsilci genel bir sürümünü kullanıma sunmaktadır <xref:System.EventHandler%601>. Aşağıdaki örnekler, her iki sürümünü de kullanmayı gösterir.  
  
 Tanımladığınız sınıflarda olayları herhangi geçerli temsilci türü, bir değer döndürmesi bile temsilciler dayalı olabilir ancak genellikle için olaylarınızı temel önerilir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] kullanarak düzeni <xref:System.EventHandler>, aşağıdaki örnekte gösterildiği gibi.  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a>EventHandler deseni temel alınarak olayları yayımlamak için  
  
1.  (Bu adımı atlayın ve, olay ile özel verileri göndermek yoksa adım 3a gidin.) Özel verilerinizi yayımcısı ve abonesi sınıflarına görünür bir kapsamda için sınıf bildirme. Ardından, özel olay verilerini tutacak gerekli üyeleri ekleyin. Bu örnekte, basit bir dize döndürdü.  
  
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
  
2.  (Genel sürümünü kullanıyorsanız bu adımı atlayın <xref:System.EventHandler%601> .) Bir temsilci yayımlama sınıfınızda bildirin. İle biten bir ad verin *EventHandler*. İkinci parametre, özel EventArgs türünü belirtir.  
  
    ```csharp  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3.  Olay yayımlama sınıfınızda aşağıdaki adımlardan birini kullanarak bildirin.  
  
    1.  Olay türü özel bir EventArgs sınıf varsa, genel olmayan OlayÝþleyicisi olacaktır. İçinde zaten bildirildiğinden temsilci bildirme gerekmez <xref:System> C# projenize oluşturduğunuzda, dahil edilen ad alanı. Yayımcı sınıfa aşağıdaki kodu ekleyin.  
  
        ```csharp  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2.  Genel olmayan sürümünü kullanıyorsanız, <xref:System.EventHandler> ve türetilen özel bir sınıf sahip <xref:System.EventArgs>, yayımlama sınıfınız içindeki, olay bildirme ve 2. adımda, temsilci türü olarak kullanın.  
  
        ```csharp  
        public event CustomEventHandler RaiseCustomEvent;  
        ```  
  
    3.  Genel sürümünü kullanıyorsanız, özel bir temsilci gerekmez. Bunun yerine, yayımlama sınıfınızda olay türü olarak belirttiğiniz `EventHandler<CustomEventArgs>`, köşeli parantez arasında kendi sınıfın adını değiştirerek.  
  
        ```csharp  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, özel bir EventArgs sınıf kullanarak önceki adımları gösterir ve <xref:System.EventHandler%601> olay türü.  
  
 [!code-csharp[csProgGuideEvents#2](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-publish-events-that-conform-to-net-framework-guidelines_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Delegate>  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Olayları](../../../csharp/programming-guide/events/index.md)  
 [Temsilciler](../../../csharp/programming-guide/delegates/index.md)
