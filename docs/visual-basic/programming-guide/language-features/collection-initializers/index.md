---
title: "Koleksiyon Başlatıcıları (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.CollectionInitializer
helpviewer_keywords: collection initializers [Visual Basic]
ms.assetid: a9290329-77b0-4fdf-ae75-8fc17287f469
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5ec0179df50df453d6058a4b910d17561394140d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="collection-initializers-visual-basic"></a>Koleksiyon Başlatıcıları (Visual Basic)
*Koleksiyon başlatıcıları* bir koleksiyon oluşturun ve başlangıç değerleri kümesi ile doldurmak sağlar kısaltılmış bir sözdizimi sağlar. Koleksiyon başlatıcıları bilinen değerler, örneğin, menü seçeneklerini veya kategorileri, bir başlangıç sayısal değerleri kümesi, statik gün veya ay adları veya gibi coğrafi konumlar gibi dizelerinin listesini listesi koleksiyondan oluştururken yararlı bir doğrulama için kullanılan durumları listesi.  
  
 Koleksiyonlar hakkında daha fazla bilgi için bkz: [koleksiyonları](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b).  
  
 Kullanarak bir koleksiyon Başlatıcısı tanımlamak `From` anahtar sözcüğünü kaşlı ayraç (`{}`). Bu bölümünde açıklanan dizi değişmez değer sözdizimine benzer [diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md). Aşağıdaki örnekler, koleksiyon başlatıcıları koleksiyonlar oluşturmak üzere kullanmak için çeşitli yollar gösterir.  
  
 [!code-vb[VbVbalrCollectionInitializers#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#1)]  
  
> [!NOTE]
>  C# koleksiyon başlatıcıları de sağlar. C# koleksiyon başlatıcıları Visual Basic koleksiyon başlatıcıları ile aynı işlevselliği sağlar. C# koleksiyon başlatıcıları hakkında daha fazla bilgi için bkz: [nesne ve koleksiyon başlatıcıları](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
## <a name="syntax"></a>Sözdizimi  
 Koleksiyon Başlatıcısı ayraç içine virgülle ayrılmış değerler listesini oluşur (`{}`), öncesinde tarafından `From` aşağıdaki kodda gösterildiği gibi anahtar.  
  
 [!code-vb[VbVbalrCollectionInitializers#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#2)]  
  
 Oluştururken bir koleksiyon gibi bir <xref:System.Collections.Generic.List%601> veya <xref:System.Collections.Generic.Dictionary%602>, aşağıdaki kodda gösterildiği gibi koleksiyon başlatıcısı önce koleksiyon türü sağlamanız gerekir.  
  
 [!code-vb[VbVbalrCollectionInitializers#13](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#13)]  
  
> [!NOTE]
>  Koleksiyon Başlatıcısı ve nesne Başlatıcı aynı koleksiyonu nesneyi başlatmak için birleştiremez. Nesne başlatıcıları koleksiyon Başlatıcısı nesneleri başlatmak için kullanabilirsiniz.  
  
## <a name="creating-a-collection-by-using-a-collection-intializer"></a>Bir koleksiyon Intializer kullanarak bir koleksiyon oluşturma  
 Koleksiyon Başlatıcısı kullanarak bir koleksiyon oluşturduğunuzda, koleksiyon başlatıcısı tarafından sağlanan her bir değeri uygun geçirilen `Add` koleksiyonunun yöntemi. Örneğin, oluşturduğunuz bir <xref:System.Collections.Generic.List%601> koleksiyon Başlatıcısı kullanarak koleksiyon Başlatıcısı her bir dize değeri için geçirilen <xref:System.Collections.Generic.List%601.Add%2A> yöntemi. Belirtilen tür, koleksiyon Başlatıcısı kullanarak bir koleksiyon oluşturmak istiyorsanız, geçerli koleksiyon türü olması gerekir. Geçerli koleksiyon türleri örneklerindendir uygulayan sınıflar <xref:System.Collections.Generic.IEnumerable%601> arabirim veya devralma <xref:System.Collections.CollectionBase> sınıfı. Belirtilen tür de kullanıma gerekir bir `Add` aşağıdaki ölçütleri karşılaması yöntemi.  
  
-   `Add` Yöntemi kullanılabilir olmalıdır, koleksiyon Başlatıcısı çağrılma kapsamının dışında. `Add` Yöntemi genel yöntemler koleksiyonunun burada erişilebilir bir senaryoda koleksiyon Başlatıcısı kullanıyorsanız ortak olması gerekmez.  
  
-   `Add` Yöntemi bir örnek üye olması gerekir veya `Shared` üyesi koleksiyon sınıfı ya da bir genişletme yöntemi.  
  
-   Bir `Add` yöntemi bulunmalıdır eşleşebilecek, koleksiyon başlatıcısı tarafından sağlanan türleri için aşırı yükleme çözümü kurallar temel alınarak.  
  
 Örneğin, aşağıdaki kod örneğinde nasıl oluşturulacağını gösteren bir `List(Of Customer)` koleksiyon Başlatıcısı kullanarak koleksiyonu. Kod çalıştırıldığında, her `Customer` nesne iletilir `Add(Customer)` genel listesinin yöntemi.  
  
 [!code-vb[VbVbalrCollectionInitializers#9](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#9)]  
  
 Aşağıdaki kod örneğinde koleksiyon Başlatıcısı kullanmayan eşdeğeri olan kodu gösterir.  
  
 [!code-vb[VbVbalrCollectionInitializers#10](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#10)]  
  
 Koleksiyon varsa bir `Add` Oluşturucusu aynı parametrelere sahip yöntemi `Customer` nesnesi, parametre değerlerini içe `Add` yöntemi bir sonraki bölümde açıklandığı gibi koleksiyon başlatıcıları içinde. Koleksiyon gibi yoksa bir `Add` yöntemi, oluşturabileceğiniz tek bir genişletme yöntemi olarak. Oluşturma örneği için bir `Add` yöntemi bir koleksiyon için bir genişletme yöntemi olarak bkz [nasıl yapılır: bir ekleme genişletme yöntemi tarafından kullanılan koleksiyon Başlatıcısı oluşturma](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md). Koleksiyon Başlatıcısı ile kullanılabilecek özel bir koleksiyon oluşturmak nasıl bir örnek için bkz: [nasıl yapılır: Koleksiyon başlatıcısı tarafından bir kullanılan koleksiyon oluşturma](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md).  
  
## <a name="nesting-collection-initializers"></a>İç içe geçme koleksiyon başlatıcıları  
 Belirli bir aşırı yüklemesinin tanımlamak için koleksiyon Başlatıcısı içindeki değerleri iç içe bir `Add` oluşturuluyor derlemesinin yöntemi. Geçirilen değerleri `Add` yöntemi virgülle ve ayraçlar içinde (`{}`), bir dizi değişmez değeri veya koleksiyon Başlatıcı yaptığınız gibi.  
  
 İç içe geçmiş değerlerini kullanarak bir koleksiyon oluşturduğunuzda iç içe geçmiş değer listesindeki her öğe için bağımsız değişken olarak geçirilen `Add` öğe türleri eşleşen yöntemi. Örneğin, aşağıdaki kod örneği oluşturur bir <xref:System.Collections.Generic.Dictionary%602> anahtarların türü olan içinde `Integer` ve değerleri türü `String`. Her iç içe geçmiş değer listeleri için eşleşen <xref:System.Collections.Generic.Dictionary%602.Add%2A> yöntemi `Dictionary`.  
  
 [!code-vb[VbVbalrCollectionInitializers#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#5)]  
  
 Önceki kod örneğinde, aşağıdaki kodu eşdeğerdir.  
  
 [!code-vb[VbVbalrCollectionInitializers#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#6)]  
  
 Yalnızca iç içe geçmiş değeri listelerinden ilk iç içe geçme düzeyini gönderilen `Add` yöntemi için koleksiyon türü. İç içe derin düzey dizi değişmez değerleri kabul edilir ve iç içe geçmiş değer listeleri için eşleşmeyen `Add` herhangi bir koleksiyonu yöntemi.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|---|---|  
|[Nasıl yapılır: oluşturmak bir koleksiyon başlatıcısı tarafından kullanılan uzantı ekleme yöntemi](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)|Adlı bir genişletme yöntemi oluşturmayı gösteren `Add` bir koleksiyon koleksiyon Başlatıcısı gelen değerlerle doldurmak için kullanılabilir.|  
|[Nasıl yapılır: Koleksiyon başlatıcısı tarafından kullanılan bir koleksiyon oluşturma](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)|Dahil ederek koleksiyon Başlatıcısı kullanımını etkinleştirmek gösterilmiştir bir `Add` uygulayan bir koleksiyon sınıfına yönteminde `IEnumerable`.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Koleksiyonları](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)  
 [Diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Nesne başlatıcıları: Adlandırılmış ve anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [New işleci](../../../../visual-basic/language-reference/operators/new-operator.md)  
 [Otomatik uygulanan özellikler](../../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)  
 [Nasıl yapılır: Visual Basic'te dizi değişkeni başlatma](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)  
 [Yerel tür çıkarımı](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Visual Basic'de LINQ'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Nasıl yapılır: öğe listesi oluşturma](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)
