---
title: "Dinamik Olarak Yükleme ve Türleri Kullanma"
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
- late binding, about late binding
- early binding
- dynamically loading and using types
- implicit late binding
- reflection, dynamically using types
ms.assetid: db985bec-5942-40ec-b13a-771ae98623dc
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3c3e2a8eac4383433888c324a3d36a6e62314462
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="dynamically-loading-and-using-types"></a>Dinamik Olarak Yükleme ve Türleri Kullanma
Yansıma gibi dil derleyicileri tarafından kullanılan altyapı sağlar [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] ve örtük geç bağlama uygulamak için JScript. Bağlama benzersiz olarak belirtilen türüne karşılık gelen bildirim (uygulama) bulma işlemidir. Bu işlem çalışma zamanında yerine derleme zamanında oluştuğunda geç bağlama adı verilir. [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)]örtük geç bağlama kodunuzda kullanmanıza olanak sağlar; Visual Basic derleyici yansıma nesne türü almak için kullandığı bir yardımcı yöntemini çağırır. Yardımcı yönteme geçirilen bağımsız değişkenler çalışma zamanında çağrılacak uygun yöntemi neden olur. Bu bağımsız değişkenler, yöntem, çağrılan yöntemi (dize) ve (nesnelerinin bir dizisi) çağrılan yönteme geçirilen bağımsız değişken adını çağırmak (nesne) örneği bulunur.  
  
 Aşağıdaki örnekte, Visual Basic derleyici yansıma örtük olarak türü derleme zamanında bilinmiyor bir nesne üzerinde bir yöntemi çağırmak için kullanır. A **HelloWorld** sınıfına sahip bir **PrintHello** "Merhaba geçirilir belirli bir metin ile birleştirilmiş World" out yazdırır yöntemi **PrintHello** yöntemi. **PrintHello** Bu örnekte adlı yöntemdir gerçekte bir <xref:System.Type.InvokeMember%2A?displayProperty=nameWithType>; Visual Basic kodu sağlar **PrintHello** (helloObj) nesnesinin türü derleme bilinirdi sanki çağrılacak yöntemi (erken bağlama) zaman yerine, çalışma zamanı (geç bağlama).  
  
```  
Imports System  
Module Hello  
    Sub Main()  
        ' Sets up the variable.  
        Dim helloObj As Object  
        ' Creates the object.  
        helloObj = new HelloWorld()  
        ' Invokes the print method as if it was early bound  
        ' even though it is really late bound.  
        helloObj.PrintHello("Visual Basic Late Bound")  
    End Sub  
End Module  
```  
  
## <a name="custom-binding"></a>Özel Bağlama  
 Örtük olarak derleyicileri tarafından geç bağlama için kullanılan ek olarak, yansıma açıkça kodda geç bağlama gerçekleştirmek için kullanılabilir.  
  
 [Ortak dil çalışma zamanı](../../../docs/standard/clr.md) birden fazla programlama dili ve bu dillerde bağlama kurallarına farklı destekler. Erken bağlama durumda kod oluşturucuları tamamen Bu bağlama kontrol edebilirsiniz. Ancak, yansıma aracılığıyla geç bağlama içinde bağlama özelleştirilmiş bağlama tarafından denetlenmesi gerekir. <xref:System.Reflection.Binder> Sınıfı seçimi ve çağırma bir üyenin özel denetim sağlar.  
  
 Özel bağlama kullanma, çalışma zamanında bir derlemeyi yüklemek, derleme, istediğiniz türünü belirtin ve yöntemleri veya erişim alan ya da bu türdeki özellikleri çağırma türleri hakkında bilgi edinin. Nesne türü kullanıcı girdisi bağımlı olduğunda gibi derleme zamanında, nesnenin türünü bilmiyorsanız bu teknik yararlıdır.  
  
 Aşağıdaki örnek, bağımsız değişken türü dönüştürme sağlayan basit bir özel bağlayıcı gösterir. İçin kod `Simple_Type.dll` ana örnek önce gelir. Yapı özen `Simple_Type.dll` ve ardından bir başvuru projede derleme zamanında dahil edin.  
  
 [!code-cpp[Conceptual.Types.Dynamic#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.dynamic/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.Dynamic#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.dynamic/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.Dynamic#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.dynamic/vb/source1.vb#1)]  
  
### <a name="invokemember-and-createinstance"></a>InvokeMember ve CreateInstance  
 Kullanım <xref:System.Type.InvokeMember%2A?displayProperty=nameWithType> bir türünün bir üyesi çağırmak için. **CreateInstance** gibi çeşitli yöntemleri sınıfları <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> ve <xref:System.Reflection.Assembly.CreateInstance%2A?displayProperty=nameWithType>, özelleştirilmiş formlar, **InvokeMember** belirtilen türe ait yeni kopyalarını oluşturun. **Bağlayıcı** sınıfı bu yöntemler aşırı çözümleme ve bağımsız değişkeni zorlama için kullanılır.  
  
 Aşağıdaki örnek, bağımsız değişken zorlama (tür dönüştürme) ve üye seçimi üç olası birleşimlerini gösterir. Servis talebi 1'de, herhangi bir bağımsız değişken zorlama veya üye seçim gereklidir. Servis talebi 2'de yalnızca üye seçimi gereklidir. Servis talebi 3'te yalnızca bağımsız değişken zorlama gereklidir.  
  
 [!code-cpp[Conceptual.Types.Dynamic#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.dynamic/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.Dynamic#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.dynamic/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.Dynamic#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.dynamic/vb/source2.vb#2)]  
  
 Aynı ada sahip birden fazla üye kullanılabilir olduğunda aşırı çözümlemesi gereklidir. <xref:System.Reflection.Binder.BindToMethod%2A?displayProperty=nameWithType> Ve <xref:System.Reflection.Binder.BindToField%2A?displayProperty=nameWithType> yöntemleri bağlama için tek bir üyeyi çözmek için kullanılır. **Binder.BindToMethod** de özelliği çözüm aracılığıyla sağlanır **almak** ve **ayarlamak** özellik erişimcisi.  
  
 **BindToMethod** döndürür <xref:System.Reflection.MethodBase> çağırmak için veya bir null başvuru (**hiçbir şey** Visual Basic'te) gibi bir çağrı mümkünse. **MethodBase'den** değeri olması gerekmez türlerden içinde yer alan dönmek *eşleşen* parametresi, normalde böyle olmasına rağmen.  
  
 ByRef bağımsız değişkenleri mevcut olduğunda, çağıran geri almak isteyebilirsiniz. Bu nedenle, **bağlayıcı** , bağımsız değişken dizisi özgün biçimine eşlemek bir istemcinin verir **BindToMethod** bağımsız değişkeni dizi yönetilebilir. Bunu yapmak için çağıran bağımsız değişkenlerin sırası değiştirilmemiştir garanti gerekir. Bağımsız değişken adıyla geçirildiğinde **bağlayıcı** bağımsız değişken dizisi ve diğer bir deyişle ne çağıran görür yeniden sıralar. Daha fazla bilgi için bkz. <xref:System.Reflection.Binder.ReorderArgumentArray%2A?displayProperty=nameWithType>.  
  
 Kullanılabilir üyeler sayıda türü veya herhangi bir taban türü tanımlı bu üyeler vardır. Varsa <xref:System.Reflection.BindingFlags> belirtilirse, hiçbir erişilebilirlik üyeleri kümesinde döndürülecek. Varsa **BindingFlags.NonPublic** belirtilmezse, bağlayıcı erişilebilirlik kuralları zorlamak gerekir. Belirtirken **ortak** veya **özel** bağlama bayrağını da belirtmeniz gerekir **örneği** veya **statik** bayrağı veya no bağlama üyeleri döndürülür.  
  
 Verilen ada sahip yalnızca bir üye ise, bir geri çağırma gereklidir ve bağlama o yöntemi yapılır. Durum 1 kod örneği, bu nokta gösterilmektedir: yalnızca bir **PrintBob** yöntemi kullanılabilir ve bu nedenle hiçbir geri çağırma gereklidir.  
  
 Kullanılabilir kümesinde birden fazla üye ise, tüm bu yöntemleri geçirilecek **BindToMethod**, uygun yöntemi seçer ve döndürür. Kod örneği, servis talebi 2'de adlı iki yöntem vardır **PrintValue**. Uygun yöntemi çağrısı tarafından seçilen **BindToMethod**.  
  
 <xref:System.Reflection.Binder.ChangeType%2A>Seçilen yöntemin biçimsel bağımsız değişkenler türüne gerçek bağımsız değişkenler dönüştüren bağımsız değişkeni zorlama (tür dönüştürme) gerçekleştirir. **ChangeType** türlerinin tam olarak eşleşmesi olsa bile her bağımsız değişkeni için çağrılır.  
  
 Kod örneği, gerçek bağımsız değişken türü, servis talebi 3'te **dize** "5.5" değerine sahip bir yapısal bağımsız değişken türü olan bir yönteme geçirilen **çift**. Çağrı başarılı olması "5.5" dize değerini bir çift değere dönüştürülmesi gerekir. **ChangeType** bu dönüştürme gerçekleştirir.  
  
 **ChangeType** yalnızca kayıpsız gerçekleştirir veya [zorlamayı genişletme](../../../docs/standard/base-types/type-conversion.md)aşağıdaki tabloda gösterildiği gibi.  
  
|Kaynak türü|Hedef türü|  
|-----------------|-----------------|  
|Herhangi bir türü|Temel türü|  
|Herhangi bir türü|Implements arabirimi|  
|Char|UInt16 UInt32, Int32, UInt64, Int64, tek, çift|  
|Bayt|Char, UInt16, Int16, UInt32, Int32, UInt64, Int64, tek, çift|  
|SByte|Int16, Int32, Int64, tek, çift|  
|UInt16|UInt32, Int32, UInt64, Int64, tek, çift|  
|Int16|Int32, Int64, tek, çift|  
|UInt32|UInt64, Int64, tek, çift|  
|Int32|Int64, tek ve çift|  
|UInt64|Tek, çift|  
|Int64|Tek, çift|  
|Tek|Çift|  
|Nonreference türü|Başvuru türü|  
  
 <xref:System.Type> Sınıfına sahip **almak** türünde parametre kullanan yöntemleri **bağlayıcı** belirli bir üye başvuruları çözümlenemedi. <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType>, <xref:System.Type.GetMethod%2A?displayProperty=nameWithType>, ve <xref:System.Type.GetProperty%2A?displayProperty=nameWithType> bu üye için imza bilgilerini sağlayarak geçerli türünün belirli bir üyesi arayın. <xref:System.Reflection.Binder.SelectMethod%2A?displayProperty=nameWithType>ve <xref:System.Reflection.Binder.SelectProperty%2A?displayProperty=nameWithType> uygun yöntemleri verilen imza bilgilerinin seçin açın geri çağrıldı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Type.InvokeMember%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
 [Tür bilgilerini görüntüleme](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)  
 [.NET Framework'te tür dönüştürme](../../../docs/standard/base-types/type-conversion.md)
