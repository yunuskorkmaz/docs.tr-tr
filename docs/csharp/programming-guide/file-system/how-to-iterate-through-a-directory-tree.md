---
title: 'Nasıl yapılır: Dizin Ağacı ile Yineleme (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- iterating through folders [C#]
- file iteration [C#]
ms.assetid: c4be4a75-6b1b-46a7-9d38-bab353091ed7
ms.openlocfilehash: 8222985e803972fb8d19159cfeaad93c9b08954d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327479"
---
# <a name="how-to-iterate-through-a-directory-tree-c-programming-guide"></a>Nasıl yapılır: Dizin Ağacı ile Yineleme (C# Programlama Kılavuzu)
Her iç içe alt herhangi bir derinliğe bir belirtilen kök klasörü altında her dosyaya erişmek deyimi "dizin ağacı yinelemek" anlamına gelir. Mutlaka her dosyayı açmak gerekmez. Dosya veya alt dizini olarak adını alıp bir `string`, veya biçiminde ek bilgi almak bir <xref:System.IO.FileInfo?displayProperty=nameWithType> veya <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> nesne.  
  
> [!NOTE]
>  Windows'da koşulları "dizin" ve "klasörü" birbirlerinin yerine kullanılır. Çoğu belgeleri ve kullanıcı arabirimi metin "klasörü," terimini kullanır ancak [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sınıf kitaplığı "directory" terimini kullanır  
  
 En basit durumda, bildiğiniz belirli belirtilen kökü altındaki tüm dizinler için erişim izinlerine sahip kullanabileceğiniz `System.IO.SearchOption.AllDirectories` bayrağı. Bu bayrak belirtilen desenle eşleşen tüm iç içe alt dizinleri döndürür. Aşağıdaki örnekte bu bayrak kullanmayı gösterir.  
  
```csharp  
root.GetDirectories("*.*", System.IO.SearchOption.AllDirectories);  
```  
  
 Belirtilen kök dizinler herhangi biri neden olursa olan Bu yaklaşımda zayıflık bir <xref:System.IO.DirectoryNotFoundException> veya <xref:System.UnauthorizedAccessException>, tüm yöntemi başarısız olur ve hiçbir dizinleri döndürür. Kullandığınızda, aynı durum geçerlidir <xref:System.IO.DirectoryInfo.GetFiles%2A> yöntemi. Belirli alt klasörlerdeki bu özel durumları işlemek varsa, el ile dizin ağacında, aşağıdaki örneklerde gösterildiği gibi yol gerekir.  
  
 El ile bir dizin ağacında yol olduğunda, ilk alt dizinleri işlemek (*öncesi sipariş geçişi*), veya dosyaları ilk (*sonrası sipariş geçişi*). Ön sipariş geçişi gerçekleştirirseniz, ağacın tamamı geçerli klasörün altında doğrudan bu klasörde kendisini dosyaları üzerinden yineleme önce yol. Daha sonra bu belgedeki örneklerde sonrası sipariş geçişi gerçekleştirmek, ancak bunları öncesi sipariş geçişi gerçekleştirmek için kolayca değiştirebilirsiniz.  
  
 Başka bir yineleme veya yığın tabanlı geçişi kullanıp kullanmayacağınızı seçenektir. Bu belgenin sonraki bölümlerinde örnekler, her iki yaklaşımın gösterir.  
  
 Çeşitli dosyalar ve klasörler üzerinde işlem gerçekleştirmek varsa, yeniden düzenleme işlemi tek bir temsilci kullanarak çağırabileceği ayrı işlevler halinde tarafından bu örnekler modülarize etmek.  
  
> [!NOTE]
>  NTFS dosya sistemleri içerebilir *yeniden ayrıştırma noktalarını* biçiminde *birleşim noktaları*, *sembolik bağlantılar*, ve *sabit bağlantıları*. .NET Framework yöntemlerini gibi <xref:System.IO.DirectoryInfo.GetFiles%2A> ve <xref:System.IO.DirectoryInfo.GetDirectories%2A> bir yeniden inceleme noktası altında herhangi bir alt dizine döndürmez. Bu davranış, iki yeniden ayrıştırma noktaları birbirine başvurduğunuzda sonsuz bir döngüde girerek riski karşı korur. Genel olarak, size değil kasıtsız olarak değiştirin veya dosyaları silin emin olmak için yeniden ayrıştırma noktaları ile dağıttığınızda onaylamadığından çok dikkatli kullanmanız gerekir. Yeniden ayrıştırma noktaları üzerinden kesin bir denetim gerektiriyorsa, platform çağırma kullanma ya da uygun Win32 dosya sistemi yöntemleri doğrudan çağırmak için yerel kodu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir dizin ağacında özyineleme kullanarak yol gösterilmektedir. Özyinelemeli yaklaşım Zarif ancak dizin ağacında büyük ve iç içe ise bir yığın taşması özel durumu neden olma olasılığı vardır.  
  
 İşlenen belirli özel durumları ve her dosya veya klasör, gerçekleştirilen belirli eylemleri yalnızca örnektir. Belirli gereksinimlerinizi karşılamak için bu kodu değiştirmeniz gerekir. Daha fazla bilgi için kod yer alan yorumlara bakın.  
  
 [!code-csharp[csFilesandFolders#1](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-iterate-through-a-directory-tree_1.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dosya ve klasörlerin bir dizin ağacında özyineleme kullanmadan yinelemek gösterilmektedir. Bu teknik genel kullanan <xref:System.Collections.Generic.Stack%601> son giren ilk çıkar (LIFO) yığınında olan koleksiyon türü.  
  
 İşlenen belirli özel durumları ve her dosya veya klasör, gerçekleştirilen belirli eylemleri yalnızca örnektir. Belirli gereksinimlerinizi karşılamak için bu kodu değiştirmeniz gerekir. Daha fazla bilgi için kod yer alan yorumlara bakın.  
  
 [!code-csharp[csFilesandFolders#2](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-iterate-through-a-directory-tree_2.cs)]  
  
 Genellikle, her klasör uygulamanızı açmak için izni olup olmadığını belirlemek için test etmek çok zaman alır. Bu nedenle, kod örneğinde işlemde kısmı yalnızca kapsayan bir `try/catch` bloğu. Değiştirebileceğiniz `catch` böylece bir klasöre erişmesi reddedildiğinde, izinlerinizi yükseltmek ve yeniden erişmek çalıştığınızda engelleme. Bir kural olarak, yalnızca bilinmeyen bir durumda, uygulamanızın ayrılmadan işleyebilir bu özel durumları yakalar.  
  
 Bellek veya disk üzerindeki bir dizin ağacında içeriğini depolamanız gerekir, yalnızca depolamak için en iyi seçenek olan <xref:System.IO.FileSystemInfo.FullName%2A> özelliği (tür `string`) her dosya için. Yeni bir oluşturmak için bu dizeyi ardından kullanabilirsiniz <xref:System.IO.FileInfo> veya <xref:System.IO.DirectoryInfo> nesne gerektiğinde veya ek işleme gerektiren herhangi bir dosyayı açın.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Sağlam dosya yineleme kodu dosya sisteminin birçok karmaşıklık dikkate almanız gerekir. Windows dosya sistemi ile ilgili daha fazla bilgi için bkz: [NTFS teknik başvuru](https://technet.microsoft.com/library/81cc8a8a-bd32-4786-a849-03245d68d8e4).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IO>  
 [LINQ ve Dosya Dizinleri](../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)  
 [Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)](../../../csharp/programming-guide/file-system/index.md)
