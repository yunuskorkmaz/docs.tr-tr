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
ms.openlocfilehash: 14a9694708b36b23ecef453d530ad3b939a046ba
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130126"
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a>Nasıl yapılır: Yansıma Kullanarak Temsilci Bağlama
Derlemeleri yüklemek ve çalıştırmak için yansıma kullandığınızda, olayları bağlamak için C# `+=` işleci veya Visual Basic [AddHandler ifadesiyle](../../visual-basic/language-reference/statements/addhandler-statement.md) benzer dil özelliklerini kullanamazsınız. Aşağıdaki yordamlarda, tüm gerekli türleri yansıma aracılığıyla alarak bir olaya mevcut bir yöntemi nasıl yedekleyerek, yansıma yayma kullanarak dinamik bir yöntem oluşturma ve bir olaya bağlama işlemleri gösterilmektedir.  
  
> [!NOTE]
> Bir olay işleme temsilcisini bağlamak için başka bir yöntem için, <xref:System.Reflection.EventInfo> sınıfının <xref:System.Reflection.EventInfo.AddEventHandler%2A> yöntemi için kod örneğine bakın.  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a>Yansımayı kullanarak bir temsilciyi bağlama  
  
1. Olayları başlatan bir tür içeren bir derleme yükleyin. Derlemeler genellikle <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemiyle yüklenir. Bu örneği basit tutmak için geçerli derlemede bulunan türetilmiş bir form kullanılır, bu nedenle geçerli derlemeyi yüklemek için <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> yöntemi kullanılır.  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2. Türü temsil eden bir <xref:System.Type> nesnesi alın ve türün bir örneğini oluşturun. <xref:System.Activator.CreateInstance%28System.Type%29> yöntemi, form parametresiz bir oluşturucuya sahip olduğu için aşağıdaki kodda kullanılır. Oluşturmakta olduğunuz türün parametresiz bir Oluşturucusu yoksa kullanabileceğiniz <xref:System.Activator.CreateInstance%2A> yönteminin birkaç başka aşırı yüklemesi vardır. Yeni örnek, derleme hakkında hiçbir şeyin bilinmediğini belirten derlemeyi sürdürmek için <xref:System.Object> türü olarak depolanır. (Yansıma, adlarını önceden bilmeden bir derlemede almanızı sağlar.)  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3. Olayı temsil eden bir <xref:System.Reflection.EventInfo> nesnesi alın ve olayı işlemek için kullanılan temsilcinin türünü almak için <xref:System.Reflection.EventInfo.EventHandlerType%2A> özelliğini kullanın. Aşağıdaki kodda, <xref:System.Windows.Forms.Control.Click> olayı için bir <xref:System.Reflection.EventInfo> elde edilir.  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4. Olayı işleyen yöntemi temsil eden bir <xref:System.Reflection.MethodInfo> nesnesi alır. Bu konunun ilerleyen kısımlarında örnek bölümünde yer alan tüm program kodu, <xref:System.Windows.Forms.Control.Click> olayını işleyen <xref:System.EventHandler> temsilcisinin imzasıyla eşleşen bir yöntemi içerir, ancak çalışma zamanında dinamik yöntemler de oluşturabilirsiniz. Ayrıntılar için, dinamik bir yöntem kullanarak çalışma zamanında olay işleyicisi oluşturmak için eşlik eden yordama bakın.  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5. <xref:System.Delegate.CreateDelegate%2A> yöntemini kullanarak temsilcinin bir örneğini oluşturun. Bu yöntem statik (Visual Basic`Shared`), bu nedenle temsilci türü sağlanmalıdır. <xref:System.Reflection.MethodInfo> alan <xref:System.Delegate.CreateDelegate%2A> aşırı yüklemelerinin kullanılması önerilir.  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6. `add` erişimci yöntemini alın ve olayı bağlamak için onu çağırın. Tüm olayların, üst düzey dillerin sözdizimi tarafından gizlenen bir `add` erişimcisi ve `remove` erişimcisi vardır. Örneğin, C# olayları bağlamak için `+=` işlecini kullanır ve Visual Basic [AddHandler ifadesini](../../visual-basic/language-reference/statements/addhandler-statement.md)kullanır. Aşağıdaki kod, <xref:System.Windows.Forms.Control.Click> olayının `add` erişimcisini alır ve ona geç bağlandığını çağırır ve temsilci örneğini geçirir. Bağımsız değişkenlerin bir dizi olarak geçirilmesi gerekir.  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7. Olayı test edin. Aşağıdaki kod, kod örneğinde tanımlanan formu gösterir. Forma tıklanması olay işleyicisini çağırır.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>   
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a>Çalışma zamanında dinamik bir yöntem kullanarak olay işleyicisi oluşturmak için  
  
1. Olay işleyici yöntemleri, basit dinamik yöntemler ve yansıma yayma kullanılarak çalışma zamanında oluşturulabilir. Bir olay işleyicisi oluşturmak için temsilcinin dönüş türü ve parametre türlerine ihtiyacınız vardır. Bu, temsilcinin `Invoke` yöntemi incelenerek elde edilebilir. Aşağıdaki kod, bu bilgileri elde etmek için `GetDelegateReturnType` ve `GetDelegateParameterTypes` yöntemlerini kullanır. Bu yöntemlerin kodu, bu konunun ilerleyen kısımlarında örnek bölümünde bulunabilir.  
  
     <xref:System.Reflection.Emit.DynamicMethod>adlandırmak gerekli değildir, bu nedenle boş dize kullanılabilir. Aşağıdaki kodda, son bağımsız değişken dinamik yöntemi geçerli türle ilişkilendirir ve temsilci, `Example` sınıfının tüm ortak ve özel üyelerine erişim sağlar.  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2. Bir yöntem gövdesi oluşturun. Bu yöntem bir dize yükler, bir dizeyi alan <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> yönteminin aşırı yüklemesini çağırır, dönüş değerini yığından kapatır (işleyicinin dönüş türü olmadığından) ve döndürür. Dinamik yöntemleri yayma hakkında daha fazla bilgi için bkz. [nasıl yapılır: tanımlama ve yürütme dinamik yöntemleri](how-to-define-and-execute-dynamic-methods.md).  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3. <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> yöntemini çağırarak dinamik metodu doldurun. Olayın çağırma listesine temsilciyi eklemek için `add` erişimcisini kullanın.  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4. Olayı test edin. Aşağıdaki kod, kod örneğinde tanımlanan formu yükler. Formu tıklatmak, hem önceden tanımlanmış olay işleyicisini hem de yayınlanan olay işleyicisini çağırır.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, var olan bir yöntemi yansıma kullanarak bir olaya nasıl bağlanacağını ve ayrıca, çalışma zamanında bir yöntemi göstermek ve bir olaya bağlamak için <xref:System.Reflection.Emit.DynamicMethod> sınıfını kullanmayı gösterir.  
  
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
