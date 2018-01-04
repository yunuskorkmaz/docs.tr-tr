---
title: "Nasıl yapılır: Yansıma Kullanarak Temsilci Bağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], adding event handlers with reflection
- reflection, adding event-handler delegates
- delegates [.NET Framework], adding event handlers with reflection
ms.assetid: 076ee62d-a964-449e-a447-c31b33518b81
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ff800eb78b07fc79193c2aa8cb71a461be2fc1d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a>Nasıl yapılır: Yansıma Kullanarak Temsilci Bağlama
Yük ve derlemeler çalıştırmak için yansıma kullandığınızda gibi C# dil özellikleri kullanamazsınız `+=` işleci veya Visual Basic [AddHandler deyimi](~/docs/visual-basic/language-reference/statements/addhandler-statement.md) olaylarını bağlanmanıza. Aşağıdaki yordamlar nasıl yansıma yoluyla tüm gerekli türlerin alarak varolan bir yöntemi bir olaya bağlanacağını gösterir ve yansıma kullanarak dinamik bir yöntemi nasıl oluşturulacağını yayma ve olaya kadar bağlayın.  
  
> [!NOTE]
>  Kod örneği için bir olay işleme temsilci bağlama başka bir yol için bkz <xref:System.Reflection.EventInfo.AddEventHandler%2A> yöntemi <xref:System.Reflection.EventInfo> sınıfı.  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a>Yansıma kullanarak temsilci bağlama için  
  
1.  Olayları başlatır türünü içeren bütünleştirilmiş yükleyin. Derlemeler ile yüklenen genellikle <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi. Bu örneği basit tutmak için geçerli derleme türetilmiş bir formda kullanılır, böylece <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> yöntemi geçerli derlemesini yüklemek için kullanılır.  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2.  Alma bir <xref:System.Type> türünü temsil eden nesne ve türünün bir örneğini oluşturun. <xref:System.Activator.CreateInstance%28System.Type%29> Biçiminde varsayılan bir oluşturucu olduğundan yöntemi aşağıdaki kodda kullanılır. Diğer birçok aşırı <xref:System.Activator.CreateInstance%2A> oluşturmakta türü varsayılan bir oluşturucu yoksa kullanabileceğiniz yöntemi. Yeni örnek türü olarak depolanır <xref:System.Object> kurgu korumak için hiçbir şeyin hakkında derleme adı verilir. (Yansıma adlarını önceden bilmeden bir derlemede türleri almanızı sağlar.)  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3.  Alma bir <xref:System.Reflection.EventInfo> olayı temsil eden nesne ve kullanmak <xref:System.Reflection.EventInfo.EventHandlerType%2A> olayını işlemek için kullanılan temsilci türü alınacağı özellik. Aşağıdaki kodda bir <xref:System.Reflection.EventInfo> için <xref:System.Windows.Forms.Control.Click> olay elde edilir.  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4.  Alma bir <xref:System.Reflection.MethodInfo> olayını işler yöntemi temsil eden nesne. Bu konunun ilerleyen bölümlerinde örnek bölümüne tam program kodunda imzası eşleşen bir yöntem içerir <xref:System.EventHandler> temsilci, yürüten <xref:System.Windows.Forms.Control.Click> olay, ancak aynı zamanda üretebilir dinamik yöntemler çalışma zamanında. Ayrıntılar için dinamik bir yöntemi kullanarak çalışma zamanında bir olay işleyicisi oluşturmak için eşlik eden yordamına bakın.  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5.  Kullanarak temsilci bir örneğini oluşturmak <xref:System.Delegate.CreateDelegate%2A> yöntemi. Bu yöntem statik (`Shared` Visual Basic'te), temsilci türü sağlanmalıdır. Aşırı kullanarak <xref:System.Delegate.CreateDelegate%2A> süren bir <xref:System.Reflection.MethodInfo> önerilir.  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6.  Alma `add` erişimci yöntemi ve olay kanca kendisine çağırma. Tüm olayları sahip bir `add` erişimcisi ve `remove` üst düzey dilleri sözdizimi tarafından gizli erişimcisi. Örneğin, C# kullanan `+=` olaylar ve Visual Basic kullanan kanca işleci [AddHandler deyimi](~/docs/visual-basic/language-reference/statements/addhandler-statement.md). Aşağıdaki kod alır `add` erişimcisine <xref:System.Windows.Forms.Control.Click> olay ve onu çağırır geç temsilci örneğinde geçirme bağlama,. Bağımsız değişkenler, bir dizi olarak geçirilmelidir.  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7.  Olay sınayın. Aşağıdaki kod, aşağıdaki kod örneğinde tanımlanan formun gösterir. Formun tıklatarak olay işleyiciyi çağırır.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>   
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a>Dinamik bir yöntemi kullanarak çalışma zamanında bir olay işleyicisi oluşturmak için  
  
1.  Olay işleyici yöntemleri basit dinamik yöntemleri kullanarak çalışma zamanında oluşturulabilir ve yansıma yayma. Olay işleyici oluşturmak için dönüş türü ve temsilci parametre türleri gerekir. Bunlar temsilcinin incelenerek alınabilir `Invoke` yöntemi. Aşağıdaki kod `GetDelegateReturnType` ve `GetDelegateParameterTypes` bu bilgileri almak için yöntemleri. Bu yöntemler için kod, bu konunun ilerleyen bölümlerinde örnek bölümünde bulunabilir.  
  
     Ad için gerekli değil bir <xref:System.Reflection.Emit.DynamicMethod>, böylece boş dize kullanılabilir. Aşağıdaki kodda son bağımsız değişken dinamik yöntemi erişim tüm genel ve özel üyelerine temsilci vermiş geçerli türüyle ilişkilendiren `Example` sınıfı.  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2.  Yöntem gövdesi oluşturur. Bu yöntem bir dize yükler, aşırı yüklemesini çağırır <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> yönteminin bir dize alan POP yığından dönüş değeri (işleyicisi hiçbir dönüş türüne sahip olduğundan) ve döndürür. Dinamik yöntemleri yayma hakkında daha fazla bilgi için bkz: [nasıl yapılır: tanımlayın ve dinamik yöntemleri yürütme](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md).  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3.  Dinamik yöntemi çağrılarak tamamlamak kendi <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> yöntemi. Kullanım `add` çağırma listesine olayı için temsilci eklemek için erişimcisi.  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4.  Olay sınayın. Aşağıdaki kod, aşağıdaki kod örneğinde tanımlanan formun yükler. Formun tıklatarak verilmiş olay işleyicisi ve önceden tanımlanmış olay işleyici çağırır.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde nasıl yansıma kullanarak bir olay için varolan bir yöntemi bağlanacağını ve aynı zamanda nasıl kullanılacağını gösterir <xref:System.Reflection.Emit.DynamicMethod> çalışma zamanında bir yöntem yayma ve olaya kadar kanca sınıfı.  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   C# kodunu `using` deyimleri (`Imports` Visual Basic'te) derleme için gerekli.  
  
-   Hiçbir ek derleme başvurularını komut satırından derleme için gereklidir. Visual Studio'da bu örnek bir konsol uygulaması olduğundan System.Windows.Forms.dll'e bir başvuru eklemeniz gerekir.  
  
-   Csc.exe, vbc.exe veya cl.exe kullanarak komut satırında kodu derleyin. Visual Studio'da Kodu derlemek için bir konsol uygulama projesi şablonunda yerleştirin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.Emit.DynamicMethod>  
 <xref:System.Activator.CreateInstance%2A>  
 <xref:System.Delegate.CreateDelegate%2A>  
 [Nasıl yapılır: Dinamik Yöntemleri Tanımlama ve Yürütme](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md)  
 [Yansıma](../../../docs/framework/reflection-and-codedom/reflection.md)
