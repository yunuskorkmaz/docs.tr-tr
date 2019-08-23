---
title: 'Nasıl yapılır: Bir dizin ağacı aracılığıyla yineleme- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- iterating through folders [C#]
- file iteration [C#]
ms.assetid: c4be4a75-6b1b-46a7-9d38-bab353091ed7
ms.openlocfilehash: ec48b9ff5a9ebe352bf0361b9e52ee0fb48576a8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923976"
---
# <a name="how-to-iterate-through-a-directory-tree-c-programming-guide"></a>Nasıl yapılır: Bir dizin ağacında yineleme (C# Programlama Kılavuzu)
"Bir dizin ağacını yineleme" ifadesi, belirtilen kök klasörü altındaki her bir dosyaya her bir dosyanın herhangi bir derinliğine erişmesi anlamına gelir. Her bir dosyayı açmak zorunda değilsiniz. Dosya veya alt dizinin adını yalnızca bir `string`olarak alabilir veya bir <xref:System.IO.FileInfo?displayProperty=nameWithType> veya <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> nesnesi biçiminde ek bilgiler alabilirsiniz.  
  
> [!NOTE]
> Windows 'da, "Directory" ve "Folder" terimleri birbirinin yerine kullanılır. Çoğu belge ve Kullanıcı arabirimi metni "Folder" terimini kullanır, ancak .NET Framework sınıf kitaplığı "Dizin" terimini kullanır.  
  
 En basit durumda, belirli bir kök altındaki tüm dizinler için erişim izinleriniz olduğunu bildiğiniz, `System.IO.SearchOption.AllDirectories` bayrağını kullanabilirsiniz. Bu bayrak, belirtilen Düzenle eşleşen tüm iç içe geçmiş alt dizinleri döndürür. Aşağıdaki örnek, bu bayrağın nasıl kullanılacağını göstermektedir.  
  
```csharp  
root.GetDirectories("*.*", System.IO.SearchOption.AllDirectories);  
```  
  
 Bu yaklaşımdaki zayıflığın, belirtilen kök altındaki alt dizinlerin herhangi biri ya <xref:System.IO.DirectoryNotFoundException> <xref:System.UnauthorizedAccessException>da bir bütün yöntemin başarısız olmasına neden olur ve Dizin döndürmez. <xref:System.IO.DirectoryInfo.GetFiles%2A> Yöntemi kullandığınızda aynı değeri de geçerlidir. Bu özel durumları belirli alt klasörlerde işlemeniz gerekiyorsa, aşağıdaki örneklerde gösterildiği gibi, dizin ağacını el ile ilermalısınız.  
  
 Bir dizin ağacını el ile ilerlerinizden önce (*ön geçiş öncesi geçiş*) veya dosyaları önce (*sıra çapraz geçişi*), önce alt dizinleri işleyebilirsiniz. Bir ön sırada çapraz geçiş gerçekleştirirseniz, doğrudan o klasörün içinde olan dosyalara geçmeden önce geçerli klasörün altındaki tüm ağaca ileredersiniz. Bu belgenin ilerleyen kısımlarında yer değiştiren örnekler, son düzen çapraz geçişi gerçekleştirir, ancak bunları önceden sıralı çapraz geçiş gerçekleştirmek üzere kolayca değiştirebilirsiniz.  
  
 Diğer bir seçenek de özyineleme veya yığın tabanlı bir geçiş geçişinin kullanılıp kullanılmayacağını belirtir. Bu belgede daha sonra gelen örneklerde her iki yaklaşım gösterilmektedir.  
  
 Dosyalar ve klasörler üzerinde çeşitli işlemler gerçekleştirmeniz gerekiyorsa, işlemi tek bir temsilci kullanarak çağırabileceğiniz ayrı işlevlere yeniden düzenleyerek bu örnekleri modüle dönüştürebilirsiniz.  
  
> [!NOTE]
> NTFS dosya sistemleri, *birleşme noktaları*, *Simgesel bağlantılar*ve *sabit bağlantılar*biçiminde *yeniden ayrıştırma noktaları* içerebilir. <xref:System.IO.DirectoryInfo.GetFiles%2A> Ve<xref:System.IO.DirectoryInfo.GetDirectories%2A> gibi .NET Framework Yöntemler, yeniden ayrıştırma noktası altında herhangi bir alt dizin döndürmez. Bu davranış, iki yeniden ayrıştırma noktası birbirine başvururken sonsuz döngüye girme riskiyle karşı koruma sağlar. Genel olarak, dosyaları istem dışı olarak değiştirmeyin veya sildiğinizden emin olmak için yeniden ayrıştırma noktalarıyla uğraşdığınızda olağanüstü dikkatli olmanız gerekir. Yeniden ayrıştırma noktaları üzerinde tam denetime ihtiyacınız varsa, doğrudan ilgili Win32 dosya sistemi yöntemlerini çağırmak için platform çağırma veya yerel kod kullanın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, özyineleme kullanarak bir dizin ağacına nasıl yol gösterir. Özyinelemeli yaklaşım zarif, ancak dizin ağacı büyük ve derin iç içe ise bir yığın taşması özel durumuna neden olur.  
  
 İşlenen özel durumlar ve her dosya veya klasör üzerinde gerçekleştirilen belirli eylemler yalnızca örnek olarak sağlanır. Bu kodu, özel gereksinimlerinizi karşılayacak şekilde değiştirmelisiniz. Daha fazla bilgi için koddaki açıklamalara bakın.  
  
 [!code-csharp[csFilesandFolders#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, özyineleme kullanılmadan bir dizin ağacındaki dosyalar ve klasörler arasında nasıl yineleme yapılacağını gösterir. Bu teknik, son ilk <xref:System.Collections.Generic.Stack%601> çıkar (LIFO) yığını olan genel koleksiyon türünü kullanır.  
  
 İşlenen özel durumlar ve her dosya veya klasör üzerinde gerçekleştirilen belirli eylemler yalnızca örnek olarak sağlanır. Bu kodu, özel gereksinimlerinizi karşılayacak şekilde değiştirmelisiniz. Daha fazla bilgi için koddaki açıklamalara bakın.  
  
 [!code-csharp[csFilesandFolders#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#2)]  
  
 Uygulamanızın onu açma iznine sahip olup olmadığını anlamak için her klasörü sınamak genellikle çok zaman alır. Bu nedenle, kod örneği işlemin yalnızca bu parçasını bir `try/catch` blokta barındırır. Bir klasöre erişim izni `catch` reddedildiğinde, izinlerinizi yükseltmeyi ve sonra yeniden erişmeyi deneyerek engellemeyi değiştirebilirsiniz. Bir kural olarak, yalnızca uygulamanızı bilinmeyen bir durumda bırakmadan işleyebilmeniz için bu özel durumları yakalayın.  
  
 Bir dizin ağacının içeriğini bellekte veya diskte depolamanız gerekirse, en iyi seçenek her bir dosya için yalnızca <xref:System.IO.FileSystemInfo.FullName%2A> özelliğini (türü `string`) saklamalıdır. Daha sonra bu dizeyi, gerektiğinde yeni <xref:System.IO.FileInfo> bir veya <xref:System.IO.DirectoryInfo> nesne oluşturmak veya ek işlem gerektiren herhangi bir dosyayı açmak için kullanabilirsiniz.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Sağlam dosya yineleme kodu, dosya sisteminin birçok karmaşıklıklarını dikkate almalıdır. Windows dosya sistemi hakkında daha fazla bilgi için bkz. [NTFS 'ye genel bakış](/windows-server/storage/file-server/ntfs-overview).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO>
- [LINQ ve Dosya Dizinleri](../concepts/linq/linq-and-file-directories.md)
- [Dosya sistemi ve kayıt defteri (C# Programlama Kılavuzu)](./index.md)
