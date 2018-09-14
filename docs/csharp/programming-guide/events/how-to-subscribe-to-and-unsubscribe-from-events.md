---
title: 'Nasıl yapılır: Olaylara Abone Olma ve Aboneliği Kaldırma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
ms.openlocfilehash: e27473ca34f634f4a3125a2e87e6d0ef918a6f9d
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45560652"
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a>Nasıl yapılır: Olaylara Abone Olma ve Aboneliği Kaldırma (C# Programlama Kılavuzu)
Olay ortaya çıktığında çağrılan özel kod yazmak istediğiniz zaman, başka bir sınıf tarafından yayımlanan bir olaya abone olun. Örneğin, bir düğmenin abone `click` uygulamanızın kullanıcı düğmeye tıkladığında faydalı bir şey yapmak için olay.  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a>Visual Studio IDE kullanarak olaylarına abone olma  
  
1.  Göremiyorsanız **özellikleri** penceresi içinde **tasarım** görüntülemek için form veya denetim bir olay işleyicisi oluşturun ve istediğiniz sağ **özellikleri**.  
  
2.  Üst kısmındaki **özellikleri** penceresinde tıklayın **olayları** simgesi.  
  
3.  Örneğin, oluşturmak istediğiniz olayı çift `Load` olay.  
  
     Visual C# boş olay işleyicisi yöntemi oluşturur ve bunu kodunuza ekler. Alternatif olarak, el ile kod ekleyebilirsiniz **kod** görünümü. Örneğin, aşağıdaki kod satırlarını olduğunda çağrılacak olay işleyicisi yöntemi bildirimini `Form` sınıfı harekete geçirirse `Load` olay.  
  
     [!code-csharp[csProgGuideEvents#11](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-subscribe-to-and-unsubscribe-from-events_1.cs)]  
  
     Olaya abone için gereken kod satırının, ayrıca otomatik olarak oluşturulan `InitializeComponent` projenizi Form1.Designer.cs dosyasında yöntemi. Bunu yeniden birleştirir:  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a>Program aracılığıyla olaylarına abone olma  
  
1.  Olay için temsilci imzası olan imzayla eşleşen bir olay işleyicisi yöntemi tanımlayın. Örneğin, olay dayanıyorsa <xref:System.EventHandler> temsilci türü, aşağıdaki kod, metot taslağı temsil eder:  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2.  Toplama atama işleci kullanın (`+=`), olay işleyicisi olaya bağlamak için. Aşağıdaki örnekte adlı bir nesne olduğunu varsayın `publisher` adlı bir olaya sahip `RaiseCustomEvent`. Abone sınıfı, olaylara abone için bir yayımcı sınıf başvurusu gerektiğini unutmayın.  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     Önceki sözdizimini C# 2.0 sürümünde yeni olduğunu unutmayın. Tam olarak hangi kapsülleyerek temsilciyi açıkça oluşturulmalıdır kullanarak C# 1.0 söz dizimi eşdeğerdir `new` anahtar sözcüğü:  
  
    ```csharp
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     Bir olay işleyicisi, bir lambda ifadesi kullanılarak da eklenebilir:  
  
    ```csharp
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
        this.Click += (s,e) => { MessageBox.Show(  
           ((MouseEventArgs)e).Location.ToString());};  
    }  
    ```  
  
     Daha fazla bilgi için [nasıl yapılır: kullanım Lambda ifadeleri dış LINQ](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).  
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a>Anonim bir yöntem kullanarak olaylarına abone olma  
  
-   Daha sonra bir olay aboneliği gerekmez, toplama atama işleci kullanabilirsiniz (`+=`) bir anonim yöntem olaya bağlamak için. Aşağıdaki örnekte adlı bir nesne olduğunu varsayın `publisher` adlı bir olaya sahip `RaiseCustomEvent` ve bir `CustomEventArgs` sınıfı da tanımlanmış bir tür özel olay bilgilerini taşımak için. Abone sınıfı başvuru gerektiğini aklınızda bulundurun `publisher` kendi olaylarına abone olmak için.  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     Abone için anonim bir işlevdir kullandıysanız, kolayca bir olayın aboneliğini kaldırmak olamaz, dikkat edin önemlidir. Bu senaryoda, aboneliğinizi iptal etmek için olaya abone olduğu koda geri, anonim yöntemin bir temsilci değişkende depolamak ve ardından temsilci olaya eklemek gereklidir. Genel olarak, kodunuza daha sonraki bir noktada olay aboneliği olacaksa olaylarına abone olmak için anonim işlevler kullanmamanızı öneririz. Anonim işlevler hakkında daha fazla bilgi için bkz. [anonim işlevler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## <a name="unsubscribing"></a>Aboneliği kaldırılıyor  
 Olay işleyicisi, olay ortaya çıktığında çağrılan önlemek için olay aboneliği. Kaynak sızıntılarını önlemek için önce bir abonelik nesnesinin elden olayları aboneliği. Bir olayın aboneliğini kaldırmak kadar olay yayımlama nesnesindeki altını çok noktaya yayın temsilci abonenin olay işleyicisi yalıtan temsilci bir başvuru içeriyor. Yayımlama nesne, başvuru tutan sürece, atık toplama abone nesnenizin silinmesine neden olmaz.  
  
#### <a name="to-unsubscribe-from-an-event"></a>Bir olayın aboneliğini kaldırmak için  
  
-   Çıkarma atama işleci kullanın (`-=`) bir olayın aboneliğini kaldırmak için:  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     Bir olayın tüm abonelerine çıktınız, yayımcı sınıf içinde olay örneği kümesine `null`.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Olaylar](../../../csharp/programming-guide/events/index.md)  
- [event](../../../csharp/language-reference/keywords/event.md)  
- [Nasıl yapılır: .NET Framework Yönergeleriyle Uyumlu Olayları Yayımlama](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
- [-= İşleci (C# Başvurusu)](../../language-reference/operators/subtraction-assignment-operator.md)  
- [+= İşleci](../../../csharp/language-reference/operators/addition-assignment-operator.md)