---
title: Koleksiyon Başlatıcıları
ms.date: 07/20/2015
f1_keywords:
- vb.CollectionInitializer
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: a9290329-77b0-4fdf-ae75-8fc17287f469
ms.openlocfilehash: fbdd116298c530ae54677631eff7dac2f22c0fe2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346775"
---
# <a name="collection-initializers-visual-basic"></a>Koleksiyon Başlatıcıları (Visual Basic)

*Koleksiyon başlatıcıları* , bir koleksiyon oluşturmanızı ve bir ilk değer kümesiyle doldurmanızı sağlayan kısaltılmış bir sözdizimi sağlar. Koleksiyon başlatıcıları, bir dizi bilinen değerden (örneğin, bir menü seçenekleri veya Kategoriler listesi, bir ilk sayısal değerler kümesi, gün veya ay adları gibi) statik bir liste veya bir gibi coğrafi konumlar oluştururken faydalıdır. doğrulama için kullanılan durumların listesi.

Koleksiyonlar hakkında daha fazla bilgi için bkz. [koleksiyonlar](../../../../visual-basic/programming-guide/concepts/collections.md).

`From` anahtar sözcüğünü ve ardından küme ayraçlarını (`{}`) kullanarak bir koleksiyon başlatıcısı belirlersiniz. Bu, [diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md)bölümünde açıklanan dizi değişmez sözdizimine benzerdir. Aşağıdaki örneklerde Koleksiyonlar oluşturmak için koleksiyon başlatıcıları kullanmanın çeşitli yolları gösterilmektedir.

[!code-vb[VbVbalrCollectionInitializers#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#1)]

> [!NOTE]
> C#Ayrıca koleksiyon başlatıcıları sağlar. C#Koleksiyon Başlatıcıları Visual Basic koleksiyonu başlatıcıları ile aynı işlevleri sağlar. Koleksiyon Başlatıcıları hakkında C# daha fazla bilgi için bkz. [nesne ve koleksiyon başlatıcıları](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).

## <a name="syntax"></a>Sözdizimi

Bir koleksiyon başlatıcısı, aşağıdaki kodda gösterildiği gibi, önce `From` anahtar sözcüğünün önünde yer alan (`{}`) parantez içine alınmış bir virgülle ayrılmış değerler listesinden oluşur.

[!code-vb[VbVbalrCollectionInitializers#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#2)]

<xref:System.Collections.Generic.List%601> veya <xref:System.Collections.Generic.Dictionary%602>gibi bir koleksiyon oluşturduğunuzda, aşağıdaki kodda gösterildiği gibi koleksiyon başlatıcıdan önce koleksiyon türünü sağlamanız gerekir.

[!code-vb[VbVbalrCollectionInitializers#13](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#13)]

> [!NOTE]
> Aynı koleksiyon nesnesini başlatmak için hem koleksiyon başlatıcısı hem de bir nesne Başlatıcısı birleştiremezsiniz. Nesne başlatıcılarının bir koleksiyon başlatıcısındaki nesneleri başlatmak için kullanabilirsiniz.

## <a name="creating-a-collection-by-using-a-collection-initializer"></a>Koleksiyon Başlatıcısı kullanarak koleksiyon oluşturma

Koleksiyon Başlatıcısı kullanarak bir koleksiyon oluşturduğunuzda, koleksiyon başlatıcısında sağlanan her bir değer koleksiyonun uygun `Add` yöntemine geçirilir. Örneğin, bir koleksiyon başlatıcısı kullanarak bir <xref:System.Collections.Generic.List%601> oluşturursanız, koleksiyon başlatıcısındaki her bir dize değeri <xref:System.Collections.Generic.List%601.Add%2A> yöntemine geçirilir. Koleksiyon Başlatıcısı kullanarak bir koleksiyon oluşturmak istiyorsanız, belirtilen tür geçerli bir koleksiyon türü olmalıdır. Geçerli koleksiyon türü örnekleri, <xref:System.Collections.Generic.IEnumerable%601> arabirimini uygulayan veya <xref:System.Collections.CollectionBase> sınıfını devraldığı sınıfları içerir. Belirtilen tür Ayrıca aşağıdaki ölçütleri karşılayan bir `Add` yöntemi kullanıma sunmalıdır.

- `Add` yöntemi, koleksiyon başlatıcısının çağrıldığı kapsamdan kullanılabilir olmalıdır. Koleksiyon Başlatıcısı, koleksiyonun genel olmayan metotlarına erişilebildiği bir senaryoda kullanıyorsanız, `Add` yönteminin ortak olması gerekmez.

- `Add` yöntemi, koleksiyon sınıfının veya bir uzantı yönteminin bir örnek üyesi veya `Shared` üyesi olmalıdır.

- Bir `Add` yöntemi, aşırı yükleme çözümleme kurallarına göre, koleksiyon başlatıcısında sağlanan türlere göre eşleştirileceği olmalıdır.

 Örneğin, aşağıdaki kod örneği, bir koleksiyon başlatıcısı kullanarak bir `List(Of Customer)` koleksiyonunun nasıl oluşturulacağını göstermektedir. Kod çalıştırıldığında, her `Customer` nesnesi genel listesinin `Add(Customer)` yöntemine geçirilir.

[!code-vb[VbVbalrCollectionInitializers#9](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#9)]

Aşağıdaki kod örneği, bir koleksiyon başlatıcısı kullanmayan denk kodu gösterir.

[!code-vb[VbVbalrCollectionInitializers#10](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#10)]

Koleksiyonda, `Customer` nesnesinin oluşturucusuyla eşleşen parametrelere sahip bir `Add` yöntemi varsa, sonraki bölümde anlatıldığı gibi koleksiyon başlatıcıları içindeki `Add` yönteminin parametre değerlerini iç içe geçirebilirsiniz. Koleksiyonda böyle bir `Add` yöntemi yoksa, bir uzantı yöntemi olarak bir tane oluşturabilirsiniz. Bir koleksiyon için uzantı yöntemi olarak `Add` yönteminin nasıl oluşturulacağı hakkında bir örnek için bkz. [nasıl yapılır: koleksiyon başlatıcısı tarafından kullanılan bir uzantı ekleme yöntemi](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)oluşturma. Bir koleksiyon başlatıcısıyla kullanılabilecek özel bir koleksiyonun nasıl oluşturulacağı hakkında bir örnek için bkz. [nasıl yapılır: koleksiyon başlatıcısı tarafından kullanılan koleksiyon oluşturma](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md).

## <a name="nesting-collection-initializers"></a>Koleksiyon Başlatıcıları iç içe

Oluşturulan koleksiyon için bir `Add` yönteminin belirli bir aşırı yüklemesini tanımlamak üzere değerleri bir koleksiyon başlatıcısı içinde iç içe geçirebilirsiniz. `Add` yöntemine geçirilen değerler, bir dizi sabit değerinde veya koleksiyon başlatıcısında yaptığınız gibi, virgülle ayrılmalıdır ve küme ayracı (`{}`) içine alınmalıdır.

İç içe geçmiş değerleri kullanarak bir koleksiyon oluşturduğunuzda, iç içe değer listesinin her bir öğesi, öğe türleriyle eşleşen `Add` metoduna bir bağımsız değişken olarak geçirilir. Örneğin, aşağıdaki kod örneği, anahtarların `Integer` türünde olduğu ve değerler `String`türünde olduğu bir <xref:System.Collections.Generic.Dictionary%602> oluşturur. İç içe değer listelerinin her biri, `Dictionary`<xref:System.Collections.Generic.Dictionary%602.Add%2A> yöntemiyle eşleştirilir.

[!code-vb[VbVbalrCollectionInitializers#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#5)]

Önceki kod örneği aşağıdaki koda eşdeğerdir.

[!code-vb[VbVbalrCollectionInitializers#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#6)]

İç içe geçme düzeyinden yalnızca iç içe geçmiş değer listeleri, koleksiyon türü için `Add` metoduna gönderilir. İç içe geçme düzeyleri dizi değişmez değerleri olarak değerlendirilir ve iç içe değer listeleri herhangi bir koleksiyonun `Add` yöntemiyle eşleştirilmez.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|---|---|
|[Nasıl yapılır: Öğe Başlatıcısı Tarafından Kullanılan Bir Uzantı Ekleme Yöntemi Oluşturma](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)|Koleksiyonu bir koleksiyon başlatıcısındaki değerlerle doldurmak için kullanılabilecek `Add` adlı bir genişletme yönteminin nasıl oluşturulacağını gösterir.|
|[Nasıl yapılır: Öğe Başlatıcısı Tarafından Kullanılan Bir Koleksiyon Oluşturma](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)|`IEnumerable`uygulayan bir koleksiyon sınıfına bir `Add` yöntemi ekleyerek koleksiyon başlatıcısı 'nın nasıl kullanılacağını gösterir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyonlar](../../../../visual-basic/programming-guide/concepts/collections.md)
- [Diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Nesne Başlatıcıları: Adlandırılmış ve Anonim Tipler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [New İşleci](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Otomatik Uygulanan Özellikler](../../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)
- [Nasıl yapılır: Visual Basic dizi değişkenini başlatma](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
- [Yerel Çıkarım](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Anonim Tipler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Visual Basic LINQ 'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Nasıl yapılır: Öğe Listesi Oluşturma](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)
