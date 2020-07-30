---
title: Olaylara abone olma ve aboneliği kaldırma-C# Programlama Kılavuzu
description: Olaylara abone olma ve olayları kaldırma hakkında bilgi edinin. Visual Studio IDE 'yi kullanarak, programlı olarak veya anonim bir yöntem kullanarak olaylara abone olun.
ms.date: 07/20/2015
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
ms.openlocfilehash: f228cc2e4fd719f4d79c56d65aa45b2a3031cba7
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302093"
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a>Olaylara abone olma ve aboneliği kaldırma (C# Programlama Kılavuzu)
Bu olay ortaya çıktığında çağrılan özel kod yazmak istediğinizde, başka bir sınıf tarafından yayımlanan bir olaya abone olursunuz. Örneğin, `click` Kullanıcı düğmeye tıkladığında uygulamanızı yararlı hale getirmek için bir düğmenin olayına abone olabilirsiniz.  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a>Visual Studio IDE kullanarak olaylara abone olma  
  
1. **Özellikler** penceresini göremiyorsanız, **Tasarım** görünümü ' nde, olay işleyicisi oluşturmak istediğiniz form veya denetime sağ tıklayın ve **Özellikler**' i seçin.  
  
2. **Özellikler** penceresinin üstünde **Olaylar** simgesine tıklayın.  
  
3. Oluşturmak istediğiniz olaya çift tıklayın, örneğin `Load` olay.  
  
     Visual C# boş bir olay işleyici yöntemi oluşturur ve bunu kodunuza ekler. Alternatif olarak, **Kod görünümünde kodu el ile de ekleyebilirsiniz** . Örneğin, aşağıdaki kod satırları, `Form` sınıf olayı harekete geçirirse çağrılacak bir olay işleyicisi yöntemi bildirir `Load` .  
  
     [!code-csharp[csProgGuideEvents#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#11)]  
  
     Olaya abone olmak için gereken kod satırı, `InitializeComponent` projenizdeki Form1.Designer.cs dosyasındaki yönteminde de otomatik olarak oluşturulur. Şuna benzer:  
  
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
  
2. `+=`Olaya bir olay işleyicisi iliştirmek için ekleme atama işlecini () kullanın. Aşağıdaki örnekte adlı bir nesnesinin adlı bir olayı olduğunu varsayalım `publisher` `RaiseCustomEvent` . Abone sınıfının olaylarına abone olmak için yayımcı sınıfına bir başvuru ihtiyacı olduğunu unutmayın.  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     Önceki sözdiziminin C# 2,0 ' de yeni olduğunu unutmayın. Bu, kapsülleme temsilcisinin anahtar sözcüğü kullanılarak açıkça oluşturulması gereken C# 1,0 sözdizimine tam olarak eşdeğerdir `new` :  
  
    ```csharp
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     Bir olay işleyicisi belirtmek için bir [lambda ifadesi](../statements-expressions-operators/lambda-expressions.md) de kullanabilirsiniz:
  
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
  
- Bir olayı daha sonra kaldırmak zorunda değilseniz, `+=` olaya anonim bir yöntem iliştirmek için ekleme atama işlecini () kullanabilirsiniz. Aşağıdaki örnekte, adlı bir nesnesinin adlı bir olayı olduğunu `publisher` `RaiseCustomEvent` ve bir `CustomEventArgs` sınıfın bir tür özel olay bilgilerini taşımak için de tanımlandığını varsayalım. Abone sınıfının `publisher` olaylarına abone olmak için bir başvuruya ihtiyacı olduğunu unutmayın.  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     Abone olmak için anonim bir işlev kullandıysanız, bir olaydan kolayca abonelik yapamayacağını fark etmeniz önemlidir. Bu senaryoda aboneliğinizi kaldırmak için, olaya abone olduğunuz koda geri dönmek, anonim yöntemi bir temsilci değişkeninde depolamak ve ardından temsilciyi olaya eklemek gereklidir. Genel olarak, kodunuzda daha sonraki bir noktada olay aboneliğinizi kaldırmak zorunda olmanız durumunda olaylara abone olmak için anonim işlevler kullanmayın. Anonim işlevler hakkında daha fazla bilgi için bkz. [Anonim işlevler](../statements-expressions-operators/anonymous-functions.md).  
  
## <a name="unsubscribing"></a>Aboneliği kaldırılıyor  
 Olay işleyicinizin olay ortaya çıktığında çağrılmasını engellemek için, olaydan aboneliği kaldırın. Kaynak sızıntılarını engellemek için, bir abone nesnesini atmadan önce etkinliklerden aboneliğinizi iptal etmelisiniz. Bir olaydan abonelik aboneliğini kaldırana kadar, yayımlama nesnesindeki olayı oluşturan çok noktaya yayın temsilcisi, abonenin olay işleyicisini kapsülleyen temsilciye bir başvuruya sahiptir. Yayımlama nesnesi bu başvuruyu taşıdığı sürece çöp toplama işlemi abone nesneniz silinmez.  
  
#### <a name="to-unsubscribe-from-an-event"></a>Bir olaydan aboneliğinizi kaldırmak için  
  
- `-=`Bir olaydan aboneliğinizi kaldırmak için çıkarma atama işlecini () kullanın:  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     Tüm aboneler bir olaydan aboneliği kaldırdığınızda, yayımcı sınıfındaki olay örneği olarak ayarlanır `null` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ekinlikler](./index.md)
- [olay](../../language-reference/keywords/event.md)
- [.NET yönergeleriyle uyumlu olayları yayımlama](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)
- [-ve-= işleçleri](../../language-reference/operators/subtraction-operator.md)
- [+ ve + = işleçleri](../../language-reference/operators/addition-operator.md)
