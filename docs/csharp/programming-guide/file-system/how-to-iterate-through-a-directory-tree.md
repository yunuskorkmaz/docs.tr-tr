---
title: 'Nasıl yapılır: -Dizin ağacı ile yineleme C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- iterating through folders [C#]
- file iteration [C#]
ms.assetid: c4be4a75-6b1b-46a7-9d38-bab353091ed7
ms.openlocfilehash: 070b409a7d1cc755451414d24ca2fa6002638dc0
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65585812"
---
# <a name="how-to-iterate-through-a-directory-tree-c-programming-guide"></a>Nasıl yapılır: Bir dizin ağacı ile yineleme (C# Programlama Kılavuzu)
Her iç içe geçmiş alt dizinde bir belirtilen kök klasöre herhangi derinliği her dosyaya erişmek deyimi "dizin ağacı yineleme" anlamına gelir. Mutlaka her dosyayı açmak gerekmez. Yalnızca dosya veya alt dizini olarak adını alabilirsiniz bir `string`, veya biçiminde ek bilgi almak bir <xref:System.IO.FileInfo?displayProperty=nameWithType> veya <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> nesne.  
  
> [!NOTE]
>  Windows koşulları "dizin" ve "klasörü" birbirinin yerine kullanılır. Çoğu belgelerini ve kullanıcı arabirimi metinlerini "klasörü" terimini kullanır, ancak .NET Framework sınıf kitaplığı "directory" terimini kullanır.  
  
 En basit örnekte, bildiğiniz belirli bir belirtilen kökü altındaki tüm dizinleri erişim izinlerine sahip olduğunuz kullanabileceğiniz `System.IO.SearchOption.AllDirectories` bayrağı. Bu bayrak, belirtilen desenle eşleşen tüm iç içe geçmiş alt döndürür. Aşağıdaki örnek, bu bayrak kullanma işlemini gösterir.  
  
```csharp  
root.GetDirectories("*.*", System.IO.SearchOption.AllDirectories);  
```  
  
 Belirtilen kök dizinler herhangi biri neden olursa olan zayıflık Bu yaklaşımda bir <xref:System.IO.DirectoryNotFoundException> veya <xref:System.UnauthorizedAccessException>, tüm yöntem başarısız ve yok dizinleri döndürür. Kullandığınızda, aynı durum geçerlidir <xref:System.IO.DirectoryInfo.GetFiles%2A> yöntemi. Belirli klasörlerde bu özel durumları işlemek varsa, dizin ağacında aşağıdaki örneklerde gösterildiği gibi el ile gezin gerekir.  
  
 Dizin ağacı el ile gezin, alt dizinleri ilk işleyebilir (*öncesi sırası geçişi*), veya dosyaları ilk (*sonrası sırası geçişi*). Öncesi sırası geçişi gerçekleştirirseniz, ağacın tamamı geçerli klasör altında doğrudan bu klasörde kendisini dosyaları ile Yinelem önce yol. Bu belgenin ilerleyen bölümlerinde verilen örneklerde sonrası sırası geçişi gerçekleştirmek, ancak bunları öncesi sırası geçişi gerçekleştirmek için kolayca değiştirebilirsiniz.  
  
 Başka bir yineleme veya bir yığın tabanlı geçişi kullanıp kullanmayacağınızı seçenektir. Bu belgenin ilerleyen bölümlerinde verilen örneklerde iki yaklaşımı gösterir.  
  
 Çeşitli dosyalar ve klasörler üzerindeki işlemleri gerçekleştirmek varsa, bu örnekleri yeniden düzenleme işlemi, tek bir temsilci aracılığıyla çağırabilirsiniz ayrı işlevler halinde tarafından modülerleştirmek.  
  
> [!NOTE]
>  NTFS dosya sistemleri içerebilir *yeniden ayrıştırma noktaları* biçiminde *birleşim noktaları*, *simgesel bağlantılar*, ve *sabit bağlantılar*. .NET Framework yöntemlerini gibi <xref:System.IO.DirectoryInfo.GetFiles%2A> ve <xref:System.IO.DirectoryInfo.GetDirectories%2A> yeniden ayrıştırma noktası altında herhangi bir alt dizini döndürmez. Bu davranış, iki yeniden ayrıştırma noktası, birbirlerine başvurduğunuzda sonsuz döngüye girme riskini karşı korur. Genel olarak, yanlışlıkla değil değiştirdiğinizde ya da dosyaları silin, emin olmak için yeniden ayrıştırma noktaları ile dağıttığınızda, son derece dikkatli olun kullanmanız gerekir. Yeniden ayrıştırma noktaları üzerinde kesin denetim gerekiyorsa, platform çağırma kullanma veya uygun Win32 dosya sistemi yöntemleri doğrudan çağırmak için yerel kod.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl bir dizin ağacında özyineleme kullanarak size yol gösterir. Özyinelemeli yaklaşım şık, ancak dizin ağacında büyük ve iç içe ise bir yığın taşması özel durumuna neden olabilir.  
  
 İşlenen belirli özel durumları ve her bir dosya veya klasör üzerinde gerçekleştirilen belirli eylemler yalnızca örnek olarak verilmiştir. Belirli gereksinimlerinizi karşılamak için bu kodu değiştirmeniz gerekir. Daha fazla bilgi için koddaki açıklamalara bakın.  
  
 [!code-csharp[csFilesandFolders#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, özyineleme kullanmadan dosya ve klasörleri dizin ağacı ile yineleme gösterilmektedir. Bu tekniği kullanan genel <xref:System.Collections.Generic.Stack%601> son giren ilk çıkar (LIFO) yığında olan koleksiyon türü.  
  
 İşlenen belirli özel durumları ve her bir dosya veya klasör üzerinde gerçekleştirilen belirli eylemler yalnızca örnek olarak verilmiştir. Belirli gereksinimlerinizi karşılamak için bu kodu değiştirmeniz gerekir. Daha fazla bilgi için koddaki açıklamalara bakın.  
  
 [!code-csharp[csFilesandFolders#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#2)]  
  
 Genel olarak, uygulamanızı açmak için izni olup olmadığını belirlemek için her klasör test çok zaman alır. Bu nedenle, kod örneği bu işlemde bölümü yalnızca kapsayan bir `try/catch` blok. Değiştirebileceğiniz `catch` izinlerinizi yükseltmek ve yeniden erişmek deneyin bir klasöre erişimi reddedildiğinde, böylece engelleyin. Bir kural olarak, yalnızca bilinmeyen bir durumda, uygulamanızın çıkmadan işleyebileceği özel durumları yakalayın.  
  
 Bir dizin ağacında içeriğini bellekte veya diskte depolamanız gerekir, yalnızca depolamak için en iyi seçenek olduğu <xref:System.IO.FileSystemInfo.FullName%2A> özelliği (tür `string`) her dosya için. Bu dize daha sonra yeni bir kullanabilirsiniz <xref:System.IO.FileInfo> veya <xref:System.IO.DirectoryInfo> nesne gerektiğinde veya ek işlem gerektiren her türlü dosyayı açmak.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Sağlam bir dosya yineleme kod dosya sistemi birçok karmaşıklığını dikkate almanız gerekir. Windows dosya sistemi hakkında daha fazla bilgi için bkz. [NTFS genel bakış](/windows-server/storage/file-server/ntfs-overview).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO>
- [LINQ ve Dosya Dizinleri](../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
- [Dosya sistemi ve kayıt defteri (C# programlama Kılavuzu)](../../../csharp/programming-guide/file-system/index.md)
