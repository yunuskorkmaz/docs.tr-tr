---
title: Dizin ağacı yla nasıl yinelene - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- iterating through folders [C#]
- file iteration [C#]
ms.assetid: c4be4a75-6b1b-46a7-9d38-bab353091ed7
ms.openlocfilehash: be3931a23e7a88affcf4d0abf617ec00bd35297a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712266"
---
# <a name="how-to-iterate-through-a-directory-tree-c-programming-guide"></a>Dizin ağacı (C# Programlama Kılavuzu) aracılığıyla nasıl yineler
"Bir dizin ağacını yinele" deyimi, iç içe geçen her alt dizindeki her dosyaya, belirli bir kök klasörü altında herhangi bir derinliğe erişmek anlamına gelir. Her dosyayı mutlaka açmanız gerekmez. Dosyanın veya alt dizinin `string`adını alabilir veya bir <xref:System.IO.FileInfo?displayProperty=nameWithType> veya <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> nesne biçiminde ek bilgiler alabilirsiniz.  
  
> [!NOTE]
> Windows'da "dizin" ve "klasör" terimleri birbirinin yerine kullanılır. Çoğu belge ve kullanıcı arabirimi metni "klasör" terimini kullanır, ancak .NET Framework sınıf kitaplığı "dizin" terimini kullanır.  
  
 Belirtilen kök altında tüm dizinler için erişim izinlerine sahip olduğunuzu kesin olarak bildiğiniz en `System.IO.SearchOption.AllDirectories` basit durumda, bayrağı kullanabilirsiniz. Bu bayrak, belirtilen desenle eşleşen iç içe geçen tüm alt dizinleri döndürür. Aşağıdaki örnekte, bu bayrağın nasıl kullanılacağı gösterilmektedir.  
  
```csharp  
root.GetDirectories("*.*", System.IO.SearchOption.AllDirectories);  
```  
  
 Bu yaklaşımdaki zayıflık, belirtilen kök altındaki alt dizinlerden herhangi <xref:System.IO.DirectoryNotFoundException> <xref:System.UnauthorizedAccessException>birinin bir veya , tüm yöntembaşarısız olur ve hiçbir dizin döndürür neden olmasıdır. Yöntemi kullandığınızda <xref:System.IO.DirectoryInfo.GetFiles%2A> aynı durum geçerlidir. Belirli alt klasörlerde bu özel durumları işlemek zorundaysanız, aşağıdaki örneklerde gösterildiği gibi dizin ağacını el ile yürümeniz gerekir.  
  
 Bir dizin ağacında el ile yürüdüğünüzde, önce alt dizinleri *(ön sipariş geçişi)* veya önce dosyaları *(sipariş sonrası geçiş)* işleyebilirsiniz. Ön sipariş geçişi gerçekleştirirseniz, doğrudan o klasörün kendisinde bulunan dosyaları gerçekleştirmeden önce geçerli klasörün altındaki tüm ağacı yürütür. Bu belgenin sonraki örnekleri sipariş sonrası geçiş gerçekleştirir, ancak bunları ön sipariş geçiş gerçekleştirmek için kolayca değiştirebilirsiniz.  
  
 Başka bir seçenek özyineleme veya yığın tabanlı geçiş kullanmak olup olmadığıdır. Bu belgenin sonraki örnekleri her iki yaklaşımı da göstermektedir.  
  
 Dosya ve klasörlerde çeşitli işlemler gerçekleştirmeniz gerekiyorsa, işlemi tek bir temsilci kullanarak çağırabileceğiniz ayrı işlevlere dönüştürerek bu örnekleri modüle edebilirsiniz.  
  
> [!NOTE]
> NTFS dosya sistemleri *kavşak noktaları,* *sembolik bağlantılar*ve sabit *bağlantılar*şeklinde *reparse noktaları* içerebilir. .NET Framework gibi <xref:System.IO.DirectoryInfo.GetFiles%2A> yöntemler <xref:System.IO.DirectoryInfo.GetDirectories%2A> ve bir reparse noktası altında herhangi bir alt dizinleri döndürmez. Bu davranış, iki reparse noktası birbirine atıfta bulunduğunda sonsuz bir döngüye girme riskine karşı koruma sağlar. Genel olarak, dosyaları istemeden değiştirmediğinizden veya silmediğinizden emin olmak için telafi noktalarıyla uğraşırken çok dikkatli olmalısınız. Reparse noktaları üzerinde hassas denetime ihtiyacınız varsa, uygun Win32 dosya sistemi yöntemlerini doğrudan çağırmak için platform çağrısı veya yerel kodu kullanın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, özyineleme kullanarak dizin ağacının nasıl yürüydüğünü gösterir. Özyinelemeli yaklaşım zariftir, ancak dizin ağacı büyük ve derin iç içe yse yığın taşma özel durumu neden olabilir.  
  
 İşlenen belirli özel durumlar ve her dosya veya klasörde gerçekleştirilen belirli eylemler yalnızca örnek olarak sağlanır. Bu kodu, özel gereksinimlerinizi karşılamak üzere değiştirmeniz gerekir. Daha fazla bilgi için koddaki yorumlara bakın.  
  
 [!code-csharp[csFilesandFolders#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, özyineleme kullanmadan dizin ağacındaki dosya ve klasörler aracılığıyla nasıl yinelenebildiğini gösterir. Bu teknik, <xref:System.Collections.Generic.Stack%601> ilk çıkış (LIFO) yığınının sonuncusu olan genel toplama türünü kullanır.  
  
 İşlenen belirli özel durumlar ve her dosya veya klasörde gerçekleştirilen belirli eylemler yalnızca örnek olarak sağlanır. Bu kodu, özel gereksinimlerinizi karşılamak üzere değiştirmeniz gerekir. Daha fazla bilgi için koddaki yorumlara bakın.  
  
 [!code-csharp[csFilesandFolders#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#2)]  
  
 Uygulamanızın açma izni olup olmadığını belirlemek için her klasörü sınamak genellikle çok zaman alır. Bu nedenle, kod örneği işlemin o bölümünü bir `try/catch` blokta kapsar. Bir klasöre `catch` erişiminiz engellendiğinde, izinlerinizi yükseltmeye ve ardından yeniden erişmeye çalışacak şekilde bloğu değiştirebilirsiniz. Kural olarak, yalnızca uygulamanızı bilinmeyen bir durumda bırakmadan işleyeceğiniz özel durumları yakalayın.  
  
 Bir dizin ağacının içeriğini bellekte veya diskte depolamanız gerekiyorsa, en iyi <xref:System.IO.FileSystemInfo.FullName%2A> seçenek her `string`dosya için yalnızca özelliği (tür) depolamaktır. Daha sonra gerektiğinde yeni <xref:System.IO.FileInfo> veya nesne <xref:System.IO.DirectoryInfo> oluşturmak veya ek işleme gerektiren herhangi bir dosyayı açmak için bu dizeyi kullanabilirsiniz.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Sağlam dosya yineleme kodu, dosya sisteminin birçok karmaşıklığını dikkate almalıdır. Windows dosya sistemi hakkında daha fazla bilgi için [NTFS genel bakış](/windows-server/storage/file-server/ntfs-overview)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO>
- [LINQ ve Dosya Dizinleri](../concepts/linq/linq-and-file-directories.md)
- [Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)](./index.md)
