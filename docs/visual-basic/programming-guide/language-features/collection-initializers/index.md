---
title: Koleksiyon Başlatıcıları (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.CollectionInitializer
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: a9290329-77b0-4fdf-ae75-8fc17287f469
ms.openlocfilehash: 538efc11e477a4e90b7bca286da4ed56105d7ecb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61906834"
---
# <a name="collection-initializers-visual-basic"></a>Koleksiyon Başlatıcıları (Visual Basic)

*Koleksiyon başlatıcıları* bir koleksiyon oluşturun ve başlangıç değer kümesi ile doldurmak sağlayan bir kısaltılmış sözdizimi sağlar. Koleksiyon başlatıcıları, bilinen değerler, örneğin, menü seçeneklerini veya kategoriler, başlangıç bir sayısal değer kümesi, bir statik bir gün veya ay adları veya coğrafi konumları gibi gibi dize listesi listesi koleksiyonundan oluştururken kullanışlı bir doğrulama için kullanılan durumların listesi.

Koleksiyonlar hakkında daha fazla bilgi için bkz. [koleksiyonları](../../../../visual-basic/programming-guide/concepts/collections.md).

Koleksiyon Başlatıcısı kullanarak tanımlamak `From` anahtar sözcüğünü ayraçları (`{}`). Bu bölümünde açıklanan dizi değişmez değer sözdizimine benzer [diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md). Aşağıdaki örnekler, koleksiyon başlatıcıları koleksiyonları oluşturmak için kullanmak için çeşitli yollar gösterir.

[!code-vb[VbVbalrCollectionInitializers#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#1)]

> [!NOTE]
> C# koleksiyon başlatıcıları de sağlar. Koleksiyon başlatıcıları C#, Visual Basic koleksiyon başlatıcıları aynı işlevleri sağlar. C# koleksiyon başlatıcıları hakkında daha fazla bilgi için bkz: [nesne ve koleksiyon başlatıcıları](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).

## <a name="syntax"></a>Sözdizimi

Küme ayraçları içine alınmış bir virgülle ayrılmış değerler listesi, bir koleksiyon Başlatıcısı oluşur (`{}`), öncesinde `From` anahtar sözcüğü, aşağıdaki kodda gösterildiği gibi.

[!code-vb[VbVbalrCollectionInitializers#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#2)]

Oluşturduğunuzda, bir toplama gibi bir <xref:System.Collections.Generic.List%601> veya <xref:System.Collections.Generic.Dictionary%602>, aşağıdaki kodda gösterildiği gibi koleksiyon başlatıcısı önce koleksiyon türü sağlamalısınız.

[!code-vb[VbVbalrCollectionInitializers#13](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#13)]

> [!NOTE]
> Aynı koleksiyon nesnesini başlatmak için bir koleksiyon Başlatıcısı ile bir nesne Başlatıcı birleştirin olamaz. Nesne başlatıcıları, nesneleri bir koleksiyon başlatıcısında başlatmak için kullanabilirsiniz.

## <a name="creating-a-collection-by-using-a-collection-initializer"></a>Koleksiyon Başlatıcısı kullanarak bir koleksiyon oluşturma

Koleksiyon Başlatıcısı kullanarak bir koleksiyon oluşturduğunuzda, koleksiyon başlatıcısı tarafından sağlanan her bir değeri uygun geçirilir `Add` koleksiyonun yöntemi. Örneğin, oluşturduğunuz bir <xref:System.Collections.Generic.List%601> koleksiyon Başlatıcısı kullanarak, her koleksiyon başlatıcısı bir dize değeri geçirilir <xref:System.Collections.Generic.List%601.Add%2A> yöntemi. Belirtilen tür, bir koleksiyon Başlatıcısı kullanarak oluşturmak istiyorsanız, geçerli koleksiyon türü olması gerekir. Geçerli koleksiyon türleri uygulayan sınıflar içeren <xref:System.Collections.Generic.IEnumerable%601> arabirim veya devralınan <xref:System.Collections.CollectionBase> sınıfı. Belirtilen tür de ortaya koymalıdır bir `Add` aşağıdaki ölçütlere uyan yöntemi.

- `Add` Yöntemi kullanılabilir olmalıdır, koleksiyon Başlatıcısı çağrılan kapsam. `Add` Yöntemi ortak olmayan yöntemlere koleksiyonun burada erişilebilir bir senaryoda koleksiyon Başlatıcısı kullanıyorsanız ortak olması gerekmez.

- `Add` Yöntemi bir örnek üyesi olmalıdır veya `Shared` koleksiyon sınıfı veya bir genişletme yöntemi üyesi.

- Bir `Add` yöntemi bulunmalıdır eşleşebilecek, koleksiyon Başlatıcısı sağlanan türler için aşırı yükleme çözünürlüğü kurallarına göre.

 Örneğin, aşağıdaki kod örneğinde nasıl oluşturulacağını gösterir bir `List(Of Customer)` koleksiyon Başlatıcısı kullanarak koleksiyonu. Kod çalıştırdığınızda, her `Customer` nesnesi `Add(Customer)` genel listenin yöntemi.

[!code-vb[VbVbalrCollectionInitializers#9](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#9)]

Aşağıdaki kod örneği, bir koleksiyon Başlatıcısı kullanmaz eşdeğer kod gösterir.

[!code-vb[VbVbalrCollectionInitializers#10](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#10)]

Koleksiyon varsa bir `Add` Oluşturucusu eşleşen parametrelere sahip yöntemi `Customer` nesnesi, parametre değerlerini içe `Add` yöntemi içinde koleksiyon başlatıcıları, sonraki bölümde açıklandığı gibi. Koleksiyon gibi yoksa bir `Add` yöntemi oluşturmak için kullanabileceğiniz bir genişletme yöntemi olarak. Oluşturma örneği için bir `Add` yöntemi bir koleksiyon için bir genişletme yöntemi olarak bkz [nasıl yapılır: Oluşturma bir koleksiyon başlatıcısı tarafından kullanılan uzantı ekleme metodu](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md). Koleksiyon Başlatıcısı ile kullanılabilecek özel bir koleksiyon oluşturma örneği için bkz: [nasıl yapılır: Koleksiyon başlatıcısı tarafından kullanılan bir koleksiyon oluşturma](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md).

## <a name="nesting-collection-initializers"></a>Koleksiyon başlatıcıları iç içe geçirme

Değerleri belirli bir aşırı yüklemesini tanımlamak için bir koleksiyon Başlatıcısı içinde iç içe bir `Add` oluşturulan koleksiyon için yöntemi. Geçirilen değerlerin `Add` yöntemi virgülle ayırarak ve ayraçlar içinde (`{}`), bir dizi değişmez değeri ya da koleksiyon Başlatıcısı içinde yaptığınız gibi.

İç içe geçmiş değerleri kullanarak bir koleksiyon oluşturduğunuzda, iç içe geçmiş değer listedeki her öğe için bir bağımsız değişken olarak geçirilir `Add` öğe türleri eşleşen yöntemi. Örneğin, aşağıdaki kod örneği oluşturur bir <xref:System.Collections.Generic.Dictionary%602> türünü anahtarları olan içinde `Integer` ve türünde değerleri olan `String`. Her iç içe geçmiş değer listeleri için eşleştirilir <xref:System.Collections.Generic.Dictionary%602.Add%2A> yöntemi `Dictionary`.

[!code-vb[VbVbalrCollectionInitializers#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#5)]

Önceki kod örneğinde, aşağıdaki koda eşdeğerdir.

[!code-vb[VbVbalrCollectionInitializers#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#6)]

Yalnızca iç içe geçmiş değer listelerinden ilk iç içe geçme düzeyini gönderilen `Add` yöntemi için koleksiyon türü. Daha derin iç içe geçme düzeyi dizi değişmez değer olarak kabul edilir ve iç içe geçmiş değer listeleri için eşleşmeyen `Add` yöntemi herhangi bir koleksiyon.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|---|---|
|[Nasıl yapılır: Oluşturma bir koleksiyon başlatıcısı tarafından kullanılan uzantı ekleme metodu](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)|Adlı bir genişletme yöntemi oluşturma işlemi gösterilmektedir `Add` bir koleksiyon Başlatıcısı değerlerle doldurmak için kullanılabilir.|
|[Nasıl yapılır: Koleksiyon başlatıcısı tarafından kullanılan bir koleksiyon oluşturma](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)|Dahil ederek bir koleksiyon Başlatıcısı kullanımını etkinleştirmek gösterilmiştir bir `Add` yöntemini uygulayan bir koleksiyon sınıfı `IEnumerable`.|

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyonlar](../../../../visual-basic/programming-guide/concepts/collections.md)
- [Diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Nesne başlatıcıları: Adlandırılmış ve anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [New İşleci](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Otomatik Uygulanan Özellikler](../../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)
- [Nasıl yapılır: Visual Basic'te dizi değişkeni başlatma](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
- [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Anonim Tipler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Visual Basic'de LINQ'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Nasıl yapılır: Öğe listesi oluşturma](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)
