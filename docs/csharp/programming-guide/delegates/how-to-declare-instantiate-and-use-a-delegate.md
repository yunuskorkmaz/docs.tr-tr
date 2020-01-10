---
title: Bir temsilci C# programlama kılavuzunu bildirme, oluşturma ve kullanma
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: 7ac1d736e19c4dcf1c8408db944505c399762778
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712370"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a>Bir temsilciyi bildirme, oluşturma ve kullanma (C# Programlama Kılavuzu)
C# 1,0 ve sonraki sürümlerde, temsilciler aşağıdaki örnekte gösterildiği gibi bildirilebilecek.  
  
 [!code-csharp[csProgGuideDelegates#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#13)]  
  
 [!code-csharp[csProgGuideDelegates#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#14)]  
  
 C#2,0, aşağıdaki örnekte gösterildiği gibi önceki bildirimi yazmak için daha basit bir yol sağlar.  
  
 [!code-csharp[csProgGuideDelegates#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#32)]  
  
 C# 2,0 ve sonraki sürümlerde, aşağıdaki örnekte gösterildiği gibi bir [temsilciyi](../../language-reference/builtin-types/reference-types.md)bildirmek ve başlatmak için anonim bir yöntem kullanmak da mümkündür.  
  
 [!code-csharp[csProgGuideDelegates#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#15)]  
  
 C# 3,0 ve sonraki sürümlerde temsilciler, aşağıdaki örnekte gösterildiği gibi bir lambda ifadesi kullanılarak da bildirilebilecek ve örneklenebilir.  
  
 [!code-csharp[csProgGuideDelegates#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#31)]  
  
 Daha fazla bilgi için bkz. [lambda ifadeleri](../statements-expressions-operators/lambda-expressions.md).  
  
 Aşağıdaki örnek, bir temsilciyi bildirme, örneklendirme ve kullanma hakkında gösterilmektedir. `BookDB` sınıfı, kitap veritabanını tutan bir kitaplığı veritabanını kapsüller. Bu, veritabanındaki tüm kağıt geri kitaplarını bulan ve her biri için bir temsilci çağıran `ProcessPaperbackBooks`bir yöntem sunar. Kullanılan `delegate` türü `ProcessBookDelegate`olarak adlandırılır. `Test` sınıfı, Paperback kitaplarının başlıklarını ve ortalama fiyatını yazdırmak için bu sınıfı kullanır.  
  
 Temsilcilerin kullanımı, kitaplığı veritabanı ve istemci kodu arasındaki işlevlerin iyi bir şekilde ayrılmasını yükseltir. İstemci kodu kitaplarının nasıl depolandığını veya kitaplığı kodunun kağıt geri defterlerini nasıl bulduğunu bilmiştir. Kitaplığı kodu, her şeyi bulduktan sonra, kağıt geri defterlerinde gerçekleştirilen işleme ilişkin hiçbir bilgiye sahip değildir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDelegates#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#12)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
  
- Temsilci bildirme.  
  
     Aşağıdaki ifade yeni bir temsilci türü bildirir.  
  
     [!code-csharp[csProgGuideDelegates#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#16)]  
  
     Her temsilci türü, bağımsız değişkenlerin sayısını ve türlerini ve kapsülleyeşabolduğu yöntemlerin dönüş değeri türünü tanımlar. Bağımsız değişken türlerinin veya dönüş değeri türünün her yeni kümesi gerektiğinde, yeni bir temsilci türü bildirilmelidir.  
  
- Bir temsilciyi örnekleme.  
  
     Bir temsilci türü bildirildiğinde, bir temsilci nesnesi oluşturulmalı ve belirli bir yöntemle ilişkilendirilmelidir. Önceki örnekte, aşağıdaki örnekte olduğu gibi `PrintTitle` yöntemini `ProcessPaperbackBooks` yöntemine geçirerek bunu yapabilirsiniz:  
  
     [!code-csharp[csProgGuideDelegates#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#17)]  
  
     Bu, `Test.PrintTitle`[statik](../../language-reference/keywords/static.md) yöntemiyle ilişkili yeni bir temsilci nesnesi oluşturur. Benzer şekilde, nesne `totaller` `AddBookToTotal` statik olmayan yöntem aşağıdaki örnekte olduğu gibi geçirilir:  
  
     [!code-csharp[csProgGuideDelegates#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#18)]  
  
     Her iki durumda da `ProcessPaperbackBooks` yöntemine yeni bir temsilci nesnesi geçirilir.  
  
     Bir temsilci oluşturulduktan sonra, ilişkili olduğu yöntem hiçbir değişiklik hiçbir şekilde değişmez; temsilci nesneleri sabittir.  
  
- Temsilci çağırma.  
  
     Temsilci nesnesi oluşturulduktan sonra temsilci nesnesi genellikle temsilciyi çağıran diğer koda geçirilir. Temsilci nesnesi, temsilci nesnesinin adı kullanılarak çağrılır ve ardından temsilciye geçirilecek parantez içine alınmış bağımsız değişkenler gelir. Aşağıda bir temsilci çağrısı örneği verilmiştir:  
  
     [!code-csharp[csProgGuideDelegates#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#19)]  
  
     Bir temsilci, bu örnekte olduğu gibi zaman uyumlu olarak ya da `BeginInvoke` ve `EndInvoke` yöntemleri kullanılarak zaman uyumsuz olarak çağrılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Olaylar](../events/index.md)
- [Temsilciler](./index.md)
