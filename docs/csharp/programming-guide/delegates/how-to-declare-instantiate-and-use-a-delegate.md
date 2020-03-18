---
title: Nasıl beyan, anlık ve bir temsilci kullanmak - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: 7ac1d736e19c4dcf1c8408db944505c399762778
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712370"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a>Temsilci (C# Programlama Kılavuzu) nasıl beyan edilir, anlık olarak kullanılır ve kullanılır?
C# 1.0 ve sonraki durumlarda, delegeler aşağıdaki örnekte gösterildiği gibi bildirilebilir.  
  
 [!code-csharp[csProgGuideDelegates#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#13)]  
  
 [!code-csharp[csProgGuideDelegates#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#14)]  
  
 C# 2.0, aşağıdaki örnekte gösterildiği gibi önceki bildirimi yazmak için daha basit bir yol sağlar.  
  
 [!code-csharp[csProgGuideDelegates#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#32)]  
  
 C# 2.0 ve sonraki durumlarda, aşağıdaki örnekte gösterildiği gibi, bir [temsilciyi](../../language-reference/builtin-types/reference-types.md)bildirmek ve başlatmak için anonim bir yöntem kullanmak da mümkündür.  
  
 [!code-csharp[csProgGuideDelegates#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#15)]  
  
 C# 3.0 ve sonraki durumlarda, aşağıdaki örnekte gösterildiği gibi, bir lambda ifadesi kullanılarak delegeler de beyan edilebilir ve anında kullanılabilir.  
  
 [!code-csharp[csProgGuideDelegates#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#31)]  
  
 Daha fazla bilgi için [Lambda İfadeleri'ne](../statements-expressions-operators/lambda-expressions.md)bakın.  
  
 Aşağıdaki örnek, bir temsilciyi bildirmeyi, anlık olarak ve kullanmayı göstermektedir. Sınıf, `BookDB` kitap veritabanını koruyan bir kitapçı veritabanını kapsüller. Veritabanındaki tüm ciltsiz kitapları bulan ve her biri için bir temsilci çağıran bir yöntem `ProcessPaperbackBooks`ortaya çıkarır. Kullanılan `delegate` türe ". `ProcessBookDelegate` Sınıf, `Test` ciltsiz kitapların başlıklarını ve ortalama fiyatını yazdırmak için bu sınıfı kullanır.  
  
 Temsilcilerin kullanımı, kitapçı veritabanı ile istemci kodu arasında işlevselliğin iyi bir şekilde ayrılmasını teşvik eder. İstemci kodu, kitapların nasıl depolanır veya kitapçı kodunun ciltsiz kitapları nasıl bulduğu hakkında hiçbir bilgiye sahip değildir. Kitapçı kodunun, ciltsiz kitaplarda hangi işlemlerin yapıldığına dair hiçbir bilgisi yoktur.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDelegates#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#12)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
  
- Bir delege ilan etmek.  
  
     Aşağıdaki deyimde yeni bir temsilci türü beyan eder.  
  
     [!code-csharp[csProgGuideDelegates#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#16)]  
  
     Her temsilci türü, bağımsız değişkenlerin sayısını ve türlerini ve kapsülleebileceği yöntemlerin dönüş değerini açıklar. Yeni bir bağımsız değişken türü kümesi veya iade değeri türü gerektiğinde, yeni bir temsilci türü bildirilmelidir.  
  
- Bir temsilciyi anında.  
  
     Bir temsilci türü seçildikten sonra, bir temsilci nesnesi oluşturulmalı ve belirli bir yöntemle ilişkilendirilmelidir. Önceki örnekte, `PrintTitle` yöntemi aşağıdaki örnekte olduğu `ProcessPaperbackBooks` gibi yönteme geçirerek bunu yaparsınız:  
  
     [!code-csharp[csProgGuideDelegates#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#17)]  
  
     Bu [statik](../../language-reference/keywords/static.md) yöntemle `Test.PrintTitle`ilişkili yeni bir temsilci nesnesi oluşturur. Benzer şekilde, nesne `AddBookToTotal` `totaller` üzerindeki statik olmayan yöntem aşağıdaki örnekte olduğu gibi geçirilir:  
  
     [!code-csharp[csProgGuideDelegates#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#18)]  
  
     Her iki durumda da yönteme `ProcessPaperbackBooks` yeni bir temsilci nesnesi geçirilir.  
  
     Bir temsilci oluşturulduktan sonra, ilişkili yöntem asla değişmez; temsilci nesneleri değişmez.  
  
- Bir temsilci çağırıyorum.  
  
     Bir temsilci nesnesi oluşturulduktan sonra, temsilci nesnesi genellikle temsilciçağıracak diğer koda geçirilir. Bir temsilci nesnesi, temsilci nesnesinin adı kullanılarak çağrılır ve ardından temsilciye geçirilecek parantez içinde bağımsız değişkenler yer eder. Aşağıda bir temsilci çağrısı örneği verilmiştir:  
  
     [!code-csharp[csProgGuideDelegates#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#19)]  
  
     Bir temsilci, bu örnekte olduğu gibi eşzamanlı olarak veya kullanarak `BeginInvoke` ve `EndInvoke` yöntemlerle eşzamanlı olarak çağrılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Olaylar](../events/index.md)
- [Temsilciler](./index.md)
