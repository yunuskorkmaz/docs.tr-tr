---
title: 'Nasıl yapılır: Yansıma Kullanarak Temsilci Bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], adding event handlers with reflection
- reflection, adding event-handler delegates
- delegates [.NET Framework], adding event handlers with reflection
ms.assetid: 076ee62d-a964-449e-a447-c31b33518b81
ms.openlocfilehash: d748d9f8bdd0b4d831880548d4aceb1c77a0b0c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180499"
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a>Nasıl yapılır: Yansıma Kullanarak Temsilci Bağlama
Derlemeleri yüklemek ve çalıştırmak için yansıma kullandığınızda, olayları bağlamak için C# `+=` işleci veya Visual Basic [AddHandler ifadesiyle](../../visual-basic/language-reference/statements/addhandler-statement.md) benzer dil özelliklerini kullanamazsınız. Aşağıdaki yordamlarda, tüm gerekli türleri yansıma aracılığıyla alarak bir olaya mevcut bir yöntemi nasıl yedekleyerek, yansıma yayma kullanarak dinamik bir yöntem oluşturma ve bir olaya bağlama işlemleri gösterilmektedir.  
  
> [!NOTE]
> Bir olay işleme temsilcisini bağlamak için başka bir yöntem için, <xref:System.Reflection.EventInfo.AddEventHandler%2A> <xref:System.Reflection.EventInfo> sınıfının yöntemi için kod örneğine bakın.  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a>Yansımayı kullanarak bir temsilciyi bağlama  
  
1. Olayları başlatan bir tür içeren bir derleme yükleyin. Derlemeler genellikle <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemiyle yüklenir. Bu örneği basit tutmak için geçerli derlemede bulunan türetilmiş bir form kullanılır, bu nedenle <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> yöntem geçerli derlemeyi yüklemek için kullanılır.  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2. Türü temsil <xref:System.Type> eden bir nesne alın ve türün bir örneğini oluşturun. Yöntemi <xref:System.Activator.CreateInstance%28System.Type%29> , parametresiz bir oluşturucuya sahip olduğu için aşağıdaki kodda kullanılır. Oluşturmakta olduğunuz türün parametresiz bir Oluşturucusu yoksa <xref:System.Activator.CreateInstance%2A> kullanabileceğiniz daha fazla başka aşırı yükleme yöntemi vardır. Yeni örnek, derleme hakkında hiçbir şeyin <xref:System.Object> bilinmediğini belirten derlemeyi sürdürmek için tür olarak depolanır. (Yansıma, adlarını önceden bilmeden bir derlemede almanızı sağlar.)  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3. Olayı temsil <xref:System.Reflection.EventInfo> eden bir nesne alın ve olayı işlemek için <xref:System.Reflection.EventInfo.EventHandlerType%2A> kullanılan temsilcinin türünü almak için özelliğini kullanın. Aşağıdaki kodda, <xref:System.Windows.Forms.Control.Click> olay için bir <xref:System.Reflection.EventInfo> elde edilir.  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4. Olayı işleyen <xref:System.Reflection.MethodInfo> yöntemi temsil eden bir nesne alır. Bu konunun ilerleyen kısımlarında örnek bölümünde yer alan tüm program kodu, <xref:System.EventHandler> <xref:System.Windows.Forms.Control.Click> olayı işleyen temsilcinin imzasıyla eşleşen bir yöntemi içerir, ancak çalışma zamanında dinamik yöntemler de oluşturabilirsiniz. Ayrıntılar için, dinamik bir yöntem kullanarak çalışma zamanında olay işleyicisi oluşturmak için eşlik eden yordama bakın.  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5. <xref:System.Delegate.CreateDelegate%2A> Yöntemini kullanarak temsilcinin bir örneğini oluşturun. Bu Yöntem statiktir (`Shared` Visual Basic), bu nedenle temsilci türü sağlanmalıdır. ' A <xref:System.Delegate.CreateDelegate%2A> <xref:System.Reflection.MethodInfo> sahip olan aşırı yüklemelerin kullanılması önerilir.  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6. `add` Erişimci yöntemini alın ve olayı bağlamak için çağırın. Tüm olayların, üst `add` düzey dillerin sözdizimi `remove` tarafından gizlenen bir erişimcisi ve erişimcisi vardır. Örneğin, C# olayları bağlamak için `+=` işlecini kullanır ve Visual Basic [AddHandler ifadesini](../../visual-basic/language-reference/statements/addhandler-statement.md)kullanır. Aşağıdaki kod, `add` <xref:System.Windows.Forms.Control.Click> olayın erişimcisini alır ve temsilci örneğini geçirerek geç sınırı çağırır. Bağımsız değişkenlerin bir dizi olarak geçirilmesi gerekir.  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7. Olayı test edin. Aşağıdaki kod, kod örneğinde tanımlanan formu gösterir. Forma tıklanması olay işleyicisini çağırır.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a>Çalışma zamanında dinamik bir yöntem kullanarak olay işleyicisi oluşturmak için  
  
1. Olay işleyici yöntemleri, basit dinamik yöntemler ve yansıma yayma kullanılarak çalışma zamanında oluşturulabilir. Bir olay işleyicisi oluşturmak için temsilcinin dönüş türü ve parametre türlerine ihtiyacınız vardır. Bu, temsilcinin `Invoke` yöntemi incelenerek elde edilebilir. Aşağıdaki kod, `GetDelegateReturnType` bu bilgileri elde `GetDelegateParameterTypes` etmek için ve yöntemlerini kullanır. Bu yöntemlerin kodu, bu konunun ilerleyen kısımlarında örnek bölümünde bulunabilir.  
  
     Bir <xref:System.Reflection.Emit.DynamicMethod>adı vermek gerekli değildir, bu nedenle boş dize kullanılabilir. Aşağıdaki kodda, son bağımsız değişken dinamik yöntemi geçerli türle ilişkilendirir ve bu temsilci, `Example` sınıfın tüm ortak ve özel üyelerine erişim sağlar.  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2. Bir yöntem gövdesi oluşturun. Bu yöntem bir dize yükler, bir dizeyi alan <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> metodun aşırı yüklemesini çağırır, dönüş değerini yığından kapatır (işleyicinin dönüş türü olmadığından) ve döndürür. Dinamik yöntemleri yayma hakkında daha fazla bilgi için bkz. [nasıl yapılır: tanımlama ve yürütme dinamik yöntemleri](how-to-define-and-execute-dynamic-methods.md).  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3. <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> Yöntemini çağırarak dinamik metodu doldurun. Olayın çağırma `add` listesine temsilciyi eklemek için erişimcisini kullanın.  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4. Olayı test edin. Aşağıdaki kod, kod örneğinde tanımlanan formu yükler. Formu tıklatmak, hem önceden tanımlanmış olay işleyicisini hem de yayınlanan olay işleyicisini çağırır.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, var olan bir yöntemin yansıma kullanarak bir olaya nasıl bağlanacağını ve ayrıca, <xref:System.Reflection.Emit.DynamicMethod> çalışma zamanında bir yöntemi göstermek ve bir olaya bağlamak için sınıfını nasıl kullanacağınızı gösterir.  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Emit.DynamicMethod>
- <xref:System.Activator.CreateInstance%2A>
- <xref:System.Delegate.CreateDelegate%2A>
- [Nasıl yapılır: Dinamik Yöntemleri Tanımlama ve Yürütme](how-to-define-and-execute-dynamic-methods.md)
- [Yansıma](reflection.md)
