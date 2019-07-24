---
title: 'Nasıl yapılır: Olaylara abone olma ve aboneliği kaldırma- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
ms.openlocfilehash: 777eb3be5cbefe0a136bf49f826ad67685a8456d
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401083"
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a>Nasıl yapılır: Olaylara abone olma ve aboneliği kaldırma (C# Programlama Kılavuzu)
Bu olay ortaya çıktığında çağrılan özel kod yazmak istediğinizde, başka bir sınıf tarafından yayımlanan bir olaya abone olursunuz. Örneğin, Kullanıcı düğmeye tıkladığında uygulamanızı yararlı hale getirmek için `click` bir düğmenin olayına abone olabilirsiniz.  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a>Visual Studio IDE kullanarak olaylara abone olma  
  
1. **Özellikler** penceresini göremiyorsanız, **Tasarım** görünümü ' nde, olay işleyicisi oluşturmak istediğiniz form veya denetime sağ tıklayın ve **Özellikler**' i seçin.  
  
2. **Özellikler** penceresinin üstünde **Olaylar** simgesine tıklayın.  
  
3. Oluşturmak istediğiniz olaya çift tıklayın, örneğin `Load` olay.  
  
     Visual C# , boş bir olay işleyici yöntemi oluşturur ve bunu kodunuza ekler. Alternatif olarak, **Kod görünümünde kodu** el ile de ekleyebilirsiniz. Örneğin, aşağıdaki kod satırları, `Form` sınıf `Load` olayı harekete geçirirse çağrılacak bir olay işleyicisi yöntemi bildirir.  
  
     [!code-csharp[csProgGuideEvents#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#11)]  
  
     Olaya abone olmak için gereken kod satırı, projenizdeki Form1.Designer.cs dosyasındaki `InitializeComponent` yönteminde de otomatik olarak oluşturulur. Şuna benzer:  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a>Olaylara programlı bir şekilde abone olmak için  
  
1. İmzası, olayın temsilci imzasıyla eşleşen bir olay işleyici yöntemi tanımlayın. Örneğin, olay <xref:System.EventHandler> temsilci türünü temel alıyorsa, aşağıdaki kod yöntem saplaması ' nı temsil eder:  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2. Olaya bir olay işleyicisi iliştirmek için`+=`ekleme atama işlecini () kullanın. Aşağıdaki örnekte adlı `publisher` bir nesnesinin adlı `RaiseCustomEvent`bir olayı olduğunu varsayalım. Abone sınıfının olaylarına abone olmak için yayımcı sınıfına bir başvuru ihtiyacı olduğunu unutmayın.  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     Önceki sözdiziminin 2,0 ' de C# yeni olduğunu unutmayın. Bu, kapsülleme temsilcisinin C# `new` anahtar sözcüğü kullanılarak açıkça oluşturulması gereken 1,0 sözdizimine tam olarak eşdeğerdir:  
  
    ```csharp
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     Bir olay işleyicisi belirtmek için de bir [lambda ifadesi](../statements-expressions-operators/lambda-expressions.md) kullanabilirsiniz:
  
    ```csharp
    public Form1()  
    {  
        InitializeComponent();  
        this.Click += (s,e) =>
            {
                MessageBox.Show(((MouseEventArgs)e).Location.ToString());
            };
    }  
    ```  
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a>Anonim bir yöntem kullanarak olaylara abone olma  
  
- Bir olayı daha sonra kaldırmak zorunda değilseniz, olaya anonim bir yöntem iliştirmek için ekleme atama işlecini (`+=`) kullanabilirsiniz. Aşağıdaki örnekte, adlı `publisher` bir nesnesinin adlı `RaiseCustomEvent` bir olayı olduğunu ve bir sınıfın bir `CustomEventArgs` tür özel olay bilgilerini taşımak için de tanımlandığını varsayalım. Abone sınıfının olaylarına abone olmak için bir başvuruya `publisher` ihtiyacı olduğunu unutmayın.  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     Abone olmak için anonim bir işlev kullandıysanız, bir olaydan kolayca abonelik yapamayacağını fark etmeniz önemlidir. Bu senaryoda aboneliğinizi kaldırmak için, olaya abone olduğunuz koda geri dönmek, anonim yöntemi bir temsilci değişkeninde depolamak ve ardından temsilciyi olaya eklemek gereklidir. Genel olarak, kodunuzda daha sonraki bir noktada olay aboneliğinizi kaldırmak zorunda olmanız durumunda olaylara abone olmak için anonim işlevler kullanmayın. Anonim işlevler hakkında daha fazla bilgi için bkz. [Anonim işlevler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## <a name="unsubscribing"></a>Aboneliği kaldırılıyor  
 Olay işleyicinizin olay ortaya çıktığında çağrılmasını engellemek için, olaydan aboneliği kaldırın. Kaynak sızıntılarını engellemek için, bir abone nesnesini atmadan önce etkinliklerden aboneliğinizi iptal etmelisiniz. Bir olaydan abonelik aboneliğini kaldırana kadar, yayımlama nesnesindeki olayı oluşturan çok noktaya yayın temsilcisi, abonenin olay işleyicisini kapsülleyen temsilciye bir başvuruya sahiptir. Yayımlama nesnesi bu başvuruyu taşıdığı sürece çöp toplama işlemi abone nesneniz silinmez.  
  
#### <a name="to-unsubscribe-from-an-event"></a>Bir olaydan aboneliğinizi kaldırmak için  
  
- Bir olaydan aboneliğinizi kaldırmak için çıkarma`-=`atama işlecini () kullanın:  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     Tüm aboneler bir olaydan aboneliği kaldırdığınızda, yayımcı sınıfındaki olay örneği olarak `null`ayarlanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olaylar](../../../csharp/programming-guide/events/index.md)
- [event](../../../csharp/language-reference/keywords/event.md)
- [Nasıl yapılır: .NET Framework yönergeleriyle uyumlu olayları yayımlama](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)
- [-ve-= işleçleri](../../language-reference/operators/subtraction-operator.md)
- [+ ve + = işleçleri](../../language-reference/operators/addition-operator.md)
