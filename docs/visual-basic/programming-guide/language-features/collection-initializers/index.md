---
title: Koleksiyon Başlatıcıları
ms.date: 07/20/2015
f1_keywords:
- vb.CollectionInitializer
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: a9290329-77b0-4fdf-ae75-8fc17287f469
ms.openlocfilehash: 1d2d5adc7266faaa1636e568d6433429761eeaab
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414549"
---
# <a name="collection-initializers-visual-basic"></a>Koleksiyon Başlatıcıları (Visual Basic)

*Koleksiyon başlatıcıları* , bir koleksiyon oluşturmanızı ve bir ilk değer kümesiyle doldurmanızı sağlayan kısaltılmış bir sözdizimi sağlar. Koleksiyon başlatıcıları, bir dizi bilinen değerden koleksiyon oluştururken (örneğin, menü seçenekleri veya kategorilerinin bir listesi, bir ilk sayısal değerler kümesi, gün veya ay adları gibi) statik bir liste veya doğrulama için kullanılan durumların listesi gibi coğrafi konumlar için yararlıdır.

Koleksiyonlar hakkında daha fazla bilgi için bkz. [koleksiyonlar](../../concepts/collections.md).

Anahtar ayracını `From` ve ardından kaşlı ayraçları kullanarak bir koleksiyon başlatıcısı belirlersiniz `{}` . Bu, [diziler](../arrays/index.md)bölümünde açıklanan dizi değişmez sözdizimine benzerdir. Aşağıdaki örneklerde Koleksiyonlar oluşturmak için koleksiyon başlatıcıları kullanmanın çeşitli yolları gösterilmektedir.

[!code-vb[VbVbalrCollectionInitializers#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#1)]

> [!NOTE]
> C# Ayrıca koleksiyon başlatıcıları sağlar. C# koleksiyon başlatıcıları Visual Basic koleksiyonu başlatıcılarına benzer işlevleri sağlar. C# koleksiyon başlatıcıları hakkında daha fazla bilgi için bkz. [nesne ve koleksiyon başlatıcıları](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).

## <a name="syntax"></a>Sözdizimi

Bir koleksiyon başlatıcısı, `{}` `From` aşağıdaki kodda gösterildiği gibi, önünde anahtar sözcüğünden sonra gelen ve ayraç () içine alınmış bir virgülle ayrılmış değerler listesinden oluşur.

[!code-vb[VbVbalrCollectionInitializers#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#2)]

Veya gibi bir koleksiyon oluşturduğunuzda <xref:System.Collections.Generic.List%601> <xref:System.Collections.Generic.Dictionary%602> , aşağıdaki kodda gösterildiği gibi koleksiyon başlatıcıdan önce koleksiyon türünü sağlamanız gerekir.

[!code-vb[VbVbalrCollectionInitializers#13](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#13)]

> [!NOTE]
> Aynı koleksiyon nesnesini başlatmak için hem koleksiyon başlatıcısı hem de bir nesne Başlatıcısı birleştiremezsiniz. Nesne başlatıcılarının bir koleksiyon başlatıcısındaki nesneleri başlatmak için kullanabilirsiniz.

## <a name="creating-a-collection-by-using-a-collection-initializer"></a>Koleksiyon Başlatıcısı kullanarak koleksiyon oluşturma

Koleksiyon Başlatıcısı kullanarak bir koleksiyon oluşturduğunuzda, koleksiyon başlatıcısında sağlanan her bir değer `Add` koleksiyonun uygun yöntemine geçirilir. Örneğin, bir <xref:System.Collections.Generic.List%601> koleksiyon başlatıcısı kullanarak bir oluşturursanız, koleksiyon başlatıcısındaki her bir dize değeri <xref:System.Collections.Generic.List%601.Add%2A> yöntemine geçirilir. Koleksiyon Başlatıcısı kullanarak bir koleksiyon oluşturmak istiyorsanız, belirtilen tür geçerli bir koleksiyon türü olmalıdır. Geçerli koleksiyon türü örnekleri, <xref:System.Collections.Generic.IEnumerable%601> arabirimini uygulayan veya sınıfını devraldığı sınıfları içerir <xref:System.Collections.CollectionBase> . Belirtilen tür Ayrıca `Add` aşağıdaki ölçütlere uyan bir yöntemi kullanıma sunmalıdır.

- `Add`Yöntemi, koleksiyon başlatıcısının çağrıldığı kapsamdan kullanılabilir olmalıdır. Koleksiyon `Add` başlatıcısı, koleksiyonun genel olmayan metotlarına erişilebilen bir senaryoda kullanılıyorsa, yöntemin ortak olması gerekmez.

- `Add`Yöntem bir örnek üyesi veya `Shared` koleksiyon sınıfının üyesi ya da bir genişletme yöntemi olmalıdır.

- Bir `Add` Yöntem, aşırı yükleme çözümleme kurallarına göre, koleksiyon başlatıcısında sağlanan türlere göre eşleştirileceği olmalıdır.

 Örneğin, aşağıdaki kod örneği `List(Of Customer)` bir koleksiyon başlatıcısı kullanarak nasıl koleksiyon oluşturulacağını göstermektedir. Kod çalıştırıldığında, her `Customer` nesne `Add(Customer)` genel liste yöntemine geçirilir.

[!code-vb[VbVbalrCollectionInitializers#9](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#9)]

Aşağıdaki kod örneği, bir koleksiyon başlatıcısı kullanmayan denk kodu gösterir.

[!code-vb[VbVbalrCollectionInitializers#10](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#10)]

Koleksiyonda `Add` nesnenin oluşturucusuyla eşleşen parametrelere sahip bir yöntem varsa `Customer` , `Add` sonraki bölümde açıklandığı gibi, yöntemin parametre değerlerini koleksiyon başlatıcıları içinde iç içe geçirebilirsiniz. Koleksiyonda böyle bir `Add` Yöntem yoksa, bir uzantı yöntemi olarak bir tane oluşturabilirsiniz. `Add`Bir koleksiyon için uzantı yöntemi olarak bir yöntemin nasıl oluşturulacağı hakkında bir örnek için bkz. [nasıl yapılır: koleksiyon başlatıcısı tarafından kullanılan bir uzantı ekleme yöntemi oluşturma](how-to-create-an-add-extension-method-used-by-a-collection-initializer.md). Bir koleksiyon başlatıcısıyla kullanılabilecek özel bir koleksiyonun nasıl oluşturulacağı hakkında bir örnek için bkz. [nasıl yapılır: koleksiyon başlatıcısı tarafından kullanılan koleksiyon oluşturma](how-to-create-a-collection-used-by-a-collection-initializer.md).

## <a name="nesting-collection-initializers"></a>Koleksiyon Başlatıcıları iç içe

Oluşturulan koleksiyon için bir yöntemin belirli bir aşırı yüklemesini tanımlamak üzere değerleri bir koleksiyon başlatıcısı içinde iç içe geçirebilirsiniz `Add` . Yöntemine geçirilen değerler, `Add` `{}` bir dizi sabit değerinde veya koleksiyon başlatıcısında yaptığınız gibi, virgülle ayrılmalıdır ve küme ayracı () içine alınmalıdır.

İç içe değerler kullanarak bir koleksiyon oluşturduğunuzda, iç içe değer listesindeki her öğe, `Add` öğe türleriyle eşleşen yönteme bir bağımsız değişken olarak geçirilir. Örneğin, aşağıdaki kod örneği, <xref:System.Collections.Generic.Dictionary%602> içinde anahtarların türü olan `Integer` ve değerleri türünde olan bir oluşturur `String` . İç içe değer listelerinin her biri <xref:System.Collections.Generic.Dictionary%602.Add%2A> , için yöntemiyle eşleştirilir `Dictionary` .

[!code-vb[VbVbalrCollectionInitializers#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#5)]

Önceki kod örneği aşağıdaki koda eşdeğerdir.

[!code-vb[VbVbalrCollectionInitializers#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#6)]

İç içe geçme düzeyinden yalnızca iç içe geçmiş değer listeleri, `Add` koleksiyon türü için metoduna gönderilir. İç içe geçme düzeyleri dizi değişmez değerleri olarak değerlendirilir ve iç içe değer listeleri `Add` herhangi bir koleksiyonun yöntemiyle eşleştirilmez.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|---|---|
|[Nasıl yapılır: Öğe Başlatıcısı Tarafından Kullanılan Bir Uzantı Ekleme Yöntemi Oluşturma](how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)|`Add`Bir koleksiyonu bir koleksiyon başlatıcısındaki değerlerle doldurmak için kullanılabilecek adlı bir genişletme yönteminin nasıl oluşturulacağını gösterir.|
|[Nasıl yapılır: Öğe Başlatıcısı Tarafından Kullanılan Bir Koleksiyon Oluşturma](how-to-create-a-collection-used-by-a-collection-initializer.md)|Uygulayan bir koleksiyon sınıfına bir yöntem ekleyerek bir koleksiyon başlatıcısı kullanımını nasıl etkinleştireceğinizi gösterir `Add` `IEnumerable` .|

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyonlar](../../concepts/collections.md)
- [Diziler](../arrays/index.md)
- [Nesne Başlatıcıları: Adlandırılmış ve Anonim Türler](../objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [New Işleci](../../../language-reference/operators/new-operator.md)
- [Otomatik Uygulanan Özellikler](../procedures/auto-implemented-properties.md)
- [Nasıl yapılır: Visual Basic'te Dizi Değişkeni Başlatma](../arrays/how-to-initialize-an-array-variable.md)
- [Yerel Tür Arabirimi](../variables/local-type-inference.md)
- [Anonim Türler](../objects-and-classes/anonymous-types.md)
- [Visual Basic'de LINQ'e Giriş](../linq/introduction-to-linq.md)
- [Nasıl yapılır: Öğe Listesi Oluşturma](../../concepts/linq/how-to-create-a-list-of-items.md)
