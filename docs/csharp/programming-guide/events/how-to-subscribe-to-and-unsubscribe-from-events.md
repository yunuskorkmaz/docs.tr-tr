---
title: 'Nasıl yapılır: Olaylara Abone Olma ve Aboneliği Kaldırma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ecb65a2156f83d9da722329ff6159bb08e464eaa
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a>Nasıl yapılır: Olaylara Abone Olma ve Aboneliği Kaldırma (C# Programlama Kılavuzu)
Bu olay ortaya çıktığında çağrılan özel kod yazmanıza istediğinizde, başka bir sınıf tarafından yayımlanan bir olaya abone olun. Örneğin, bir düğmenin abone `click` uygulamanız kullanıcı düğmesini tıklattığında yararlı bir şeyler yapmak için olay.  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a>Visual Studio IDE kullanarak olaylara abone olma  
  
1.  Göremiyorsanız **özellikleri** penceresi, **tasarım** görüntülemek için form veya bir olay işleyicisi oluşturun ve seçmek istediğiniz denetimi sağ **özellikleri**.  
  
2.  Üstünde **özellikleri** penceresinde tıklatın **olayları** simgesi.  
  
3.  Örneğin, oluşturmak istediğiniz olayı çift `Load` olay.  
  
     Visual C# boş olay işleyicisi yöntemi oluşturur ve kodunuzu ekler. Alternatif olarak, el ile kod ekleyebilirsiniz **kod** görünümü. Örneğin, aşağıdaki kod satırlarını ne zaman çağrılacağı bir olay işleyicisi yöntemi bildirme `Form` sınıfı başlatır `Load` olay.  
  
     [!code-csharp[csProgGuideEvents#11](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-subscribe-to-and-unsubscribe-from-events_1.cs)]  
  
     Olaya abone olmak için gerekli kod satırı da otomatik olarak üretildi `InitializeComponent` projenizdeki Form1.Designer.cs dosyasındaki yöntemi. Bu benzer:  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a>Program aracılığıyla olaylara abone olma  
  
1.  Olayı için temsilci imza, imza eşleşen bir olay işleyicisi yöntemi tanımlayın. Örneğin, olay dayanıyorsa <xref:System.EventHandler> temsilci türü, aşağıdaki kodu yöntemi saplama temsil eder:  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2.  Toplama atama işleci kullanın (`+=`), olay işleyicisi olaya bağlamak için. Aşağıdaki örnekte, bir nesne adlı varsayın `publisher` sahip adlı bir olay `RaiseCustomEvent`. Abone sınıfı için olaylarına abone olmak için yayımcı sınıfı başvuru gerektiğini unutmayın.  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     Önceki sözdizimi C# 2. 0'yeni olduğuna dikkat edin. Tam olarak hangi kapsülleyerek temsilci açıkça oluşturulmalıdır kullanarak C# 1.0 sözdizimi eşdeğerdir `new` anahtar sözcüğü:  
  
    ```csharp
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     Olay işleyici lambda ifadesi kullanarak da eklenebilir:  
  
    ```csharp
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
        this.Click += (s,e) => { MessageBox.Show(  
           ((MouseEventArgs)e).Location.ToString());};  
    }  
    ```  
  
     Daha fazla bilgi için bkz: [nasıl yapılır: kullanım Lambda ifadeleri dış LINQ](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).  
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a>Anonim bir yöntem kullanarak olaylara abone olma  
  
-   Bir olaya daha sonra aboneliği gerekmez, toplama atama işleci kullanabilirsiniz (`+=`) adsız bir yöntem olaya bağlamak için. Aşağıdaki örnekte, bir nesne adlı varsayın `publisher` sahip adlı bir olay `RaiseCustomEvent` ve bir `CustomEventArgs` sınıfı ayrıca tanımlandı bir tür özel olay bilgilerini taşımak için. Abone sınıfı bir başvuru gerektiğini unutmayın `publisher` kendi olaylarına abone olmak için.  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     Kolayca abone adsız bir işlev kullandıysanız bir olaydan aboneliğinizi iptal edilemez olduğunu fark önemlidir. Bu senaryoda, aboneliğinizi iptal etmek için olaya abone olduğu geri kod, bir temsilci değişkende anonim yöntemi depolamak ve ardından temsilci olaya eklemek gitmek gereklidir. Genel olarak, kodunuzda daha sonraki bir noktada olay aboneliğinizi iptal etmek olacaksa olaylarına abone olmak için anonim işlevler kullanmamanızı öneririz. Anonim işlevler hakkında daha fazla bilgi için bkz: [anonim işlevler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## <a name="unsubscribing"></a>Aboneliği  
 Olay ortaya çıktığında çağrılan olay işleyicisi önlemek için olay aboneliği. Kaynak sızıntıları önlemek için bir abonelik nesnesinin dispose önce olaylarından aboneliği. Bir olay aboneliği kadar olay yayımlama nesnesindeki altını çizen çok noktaya yayın temsilci abonenin olay işleyicisi yalıtır temsilci bir başvuru içeriyor. Bu başvuru yayımlama nesnesi tutar sürece, atık toplama abone nesnenizin silmez.  
  
#### <a name="to-unsubscribe-from-an-event"></a>Bir olay aboneliğinizi iptal etmek için  
  
-   Çıkarma atama işleci kullanın (`-=`) bir olay aboneliğinizi iptal etmek için:  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     Tüm aboneler bir olaydan kaldırdınız, yayımcı sınıfı olay örneğinde kümesine `null`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Olaylar](../../../csharp/programming-guide/events/index.md)  
 [event](../../../csharp/language-reference/keywords/event.md)  
 [Nasıl yapılır: .NET Framework Yönergeleriyle Uyumlu Olayları Yayımlama](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
 [-= İşleci (C# Başvurusu)](../../language-reference/operators/subtraction-assignment-operator.md)  
 [+= İşleci](../../../csharp/language-reference/operators/addition-assignment-operator.md)