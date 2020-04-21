---
title: Etkinliklere abone olunve aboneliğinizi iptal e-Çıkış - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
ms.openlocfilehash: 0a9e2cc64da56c376445efce32e8da36ba9b6cdc
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738228"
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a>Etkinliklere abone olunve abonelikten çıkılmaz (C# Programlama Kılavuzu)
Bu olay yükseltildiğinde çağrılan özel kod yazmak istediğinizde başka bir sınıf tarafından yayımlanan bir olaya abone olabilirsiniz. Örneğin, kullanıcı düğmeyi tıklattığında `click` uygulamanızın yararlı bir şey yapmasını sağlamak için bir düğmenin etkinliğine abone olabilirsiniz.  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a>Visual Studio IDE'yi kullanarak etkinliklere abone olmak için  
  
1. **Özellikler** penceresini göremiyorsanız, **Tasarım** görünümünde, olay işleyicisi oluşturmak istediğiniz formu veya denetimi sağ tıklatın ve **Özellikler'i**seçin.  
  
2. **Özellikler** penceresinin üstünde, **Etkinlikler** simgesini tıklatın.  
  
3. Oluşturmak istediğiniz olayı ( örneğin `Load` olay) çift tıklatın.  
  
     Visual C# boş bir olay işleyicisi yöntemi oluşturur ve kodunuza ekler. Alternatif olarak **kodu Kod** görünümüne el ile ekleyebilirsiniz. Örneğin, aşağıdaki kod `Form` satırları, sınıf `Load` olayı yükselttiğinde çağrılacak bir olay işleyicisi yöntemini bildirir.  
  
     [!code-csharp[csProgGuideEvents#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#11)]  
  
     Etkinliğe abone olmak için gereken kod satırı da projenizdeki `InitializeComponent` Form1.Designer.cs dosyasındaki yöntemde otomatik olarak oluşturulur. Buna benziyor:  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a>Etkinliklere programlı abone olmak için  
  
1. İmzası olay için temsilci imzasıyla eşleşen bir olay işleyicisi yöntemi tanımlayın. Örneğin, olay <xref:System.EventHandler> temsilci türünü temel alırsa, aşağıdaki kod yöntem saplamasını temsil eder:  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2. Olay için bir`+=`olay işleyicisi eklemek için ekleme atama işleci ( ) kullanın. Aşağıdaki örnekte, adlı `publisher` bir nesnenin . `RaiseCustomEvent`adlı bir olayı olduğunu varsayalım Abone sınıfının etkinliklerine abone olmak için yayımcı sınıfına bir başvuruyapması gerektiğini unutmayın.  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     Önceki sözdiziminin C# 2.0'da yeni olduğunu unutmayın. Tam olarak c# 1.0 sözdizimi olan kapsülleme temsilci açıkça `new` anahtar sözcüğü kullanılarak oluşturulmalıdır eşdeğerdir:  
  
    ```csharp
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     Bir olay işleyicisi belirtmek için [bir lambda ifadesi](../statements-expressions-operators/lambda-expressions.md) de kullanabilirsiniz:
  
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
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a>Anonim bir yöntem kullanarak olaylara abone olmak için  
  
- Daha sonra bir etkinliğe aboneliğinizi iptal etmek zorunda kalmazsanız, olaya anonim bir yöntem eklemek için ekleme atama işlecini ()`+=`kullanabilirsiniz. Aşağıdaki örnekte, adlı `publisher` bir nesnenin adında `RaiseCustomEvent` bir `CustomEventArgs` olayı olduğunu ve bir sınıfın da bir tür özel olay bilgisi taşımak üzere tanımlandığını varsayalım. Abone sınıfının etkinliklerine abone `publisher` olmak için bir başvuruya ihtiyacı olduğunu unutmayın.  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     Abone olmak için anonim bir işlev kullandıysanız, bir etkinlikten kolayca aboneliğinizi kaldıramayacağınızı fark etmek önemlidir. Bu senaryoda aboneliği iptal etmek için, olaya abone olduğunuz koda geri dönmek, anonim yöntemi bir temsilci değişkeninde depolamak ve ardından temsilciyi olaya eklemek gerekir. Genel olarak, kodunuzda daha sonraki bir noktada etkinlikten aboneliğinizi iptal etmek zorunda kalacaksanız, olaylara abone olmak için anonim işlevler kullanmamanızı öneririz. Anonim işlevler hakkında daha fazla bilgi için [Bkz. Anonim Fonksiyonlar.](../statements-expressions-operators/anonymous-functions.md)  
  
## <a name="unsubscribing"></a>Aboneliği kaldır  
 Olay yükseltildiğinde olay işleyicinizin çağrılmasını önlemek için etkinlikten aboneliğinizi iptal edin. Kaynak sızıntılarını önlemek için, bir abone nesnesini elden çıkarmadan önce olaylardan aboneliğinizi iptal etmelisiniz. Bir etkinlikten aboneliğinizi iptal edene kadar, yayımlama nesnesindeki olayın altında yatan çok noktaya yayın temsilcisinin, abonenin olay işleyicisini kapsülleyen temsilciye bir başvurusu vardır. Yayımlama nesnesi bu başvuruyu tuttuğu sürece, çöp toplama abone nesnenizi silmez.  
  
#### <a name="to-unsubscribe-from-an-event"></a>Bir etkinlikten aboneliğinizi iptal etmek için  
  
- Bir olaydan aboneliğini`-=`iptal etmek için çıkarma atama işleci ( ) kullanın:  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     Tüm aboneler bir etkinlikten aboneliğini iptal ettiğinde, yayımcı sınıfındaki olay örneği `null`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olaylar](./index.md)
- [Olay](../../language-reference/keywords/event.md)
- [.NET Framework Yönergeleriyle uyumlu olayları yayımlama](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)
- [- ve -= operatörler](../../language-reference/operators/subtraction-operator.md)
- [+ ve += işleçleri](../../language-reference/operators/addition-operator.md)
