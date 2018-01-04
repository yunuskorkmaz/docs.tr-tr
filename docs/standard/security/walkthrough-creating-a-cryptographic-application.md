---
title: "İzlenecek Yol: Şifreleme Uygulaması Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [NET Framework], example
- cryptography [NET Framework], cryptographic application example
- cryptography [NET Framework], application example
ms.assetid: abf48c11-1e72-431d-9562-39cf23e1a8ff
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 869d35a15a028e6df09dea281ac653ab8b9a28d6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="walkthrough-creating-a-cryptographic-application"></a>İzlenecek Yol: Şifreleme Uygulaması Oluşturma
Bu kılavuz, şifrelemek ve içeriğin şifresini gösterilmiştir. Kod örnekleri, bir Windows Forms uygulaması için tasarlanmıştır. Bu uygulamayı gerçek dünya senaryoları, akıllı kart kullanma gibi gösterilmemiştir. Bunun yerine, şifreleme ve şifre çözme temelleri gösterilmektedir.  
  
 Bu kılavuz aşağıdaki yönergeleri için şifreleme kullanır:  
  
-   Kullanım <xref:System.Security.Cryptography.RijndaelManaged> sınıfı, şifrelemek ve kendi otomatik olarak oluşturulan kullanarak verilerin şifresini çözmek için bir simetrik algoritması <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> ve <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>.  
  
-   Kullanım <xref:System.Security.Cryptography.RSACryptoServiceProvider>, şifrelemek ve tarafından şifrelenmiş verilere anahtarın şifresini çözmek için bir asimetrik algoritma <xref:System.Security.Cryptography.RijndaelManaged>. Asimetrik algoritmalar, en iyi daha küçük miktarda bir anahtarı gibi veriler için kullanılır.  
  
    > [!NOTE]
    >  Diğer kişilerle şifrelenmiş içerik değişimi yerine, bilgisayarınızdaki verileri korumak istiyorsanız, kullanmayı <xref:System.Security.Cryptography.ProtectedData> veya <xref:System.Security.Cryptography.ProtectedMemory> sınıfları.  
  
 Bu konu başlığı altındaki şifreleme görevleri aşağıdaki tabloda özetlenmiştir.  
  
|Görev|Açıklama|  
|----------|-----------------|  
|Bir Windows Forms uygulaması oluşturma|Uygulamayı çalıştırmak için gerekli denetimleri listeler.|  
|Genel nesne bildirme|Yol değişkenleri, dize bildirir <xref:System.Security.Cryptography.CspParameters>ve <xref:System.Security.Cryptography.RSACryptoServiceProvider> genel bağlamında olmasını <xref:System.Windows.Forms.Form> sınıfı.|  
|Asimetrik anahtar oluşturma|Asimetrik ortak ve özel anahtar değer çifti oluşturur ve bir anahtar kapsayıcı adı atar.|  
|Bir dosya şifreleme|Dosyayı şifreler ve şifreleme için bir dosya seçmek için bir iletişim kutusu görüntüler.|  
|Bir dosyanın şifresini çözmek üzere|Dosyanın şifresini çözer ve şifre çözme için şifrelenmiş bir dosya seçmek için bir iletişim kutusu görüntüler.|  
|Bir özel anahtar alma|Anahtar kapsayıcı adı kullanarak tam anahtar çifti alır.|  
|Bir ortak anahtar dışarı aktarma|Yalnızca ortak parametreleri içeren bir XML dosyası için anahtar kaydeder.|  
|Bir ortak anahtar alma|Anahtar bir XML dosyasından anahtar kapsayıcısına yükler.|  
|Uygulamayı test etme|Bu uygulamayı test etmek için yordamları listeler.|  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   Başvurular <xref:System.IO> ve <xref:System.Security.Cryptography> ad alanları.  
  
## <a name="creating-a-windows-forms-application"></a>Bir Windows Forms uygulaması oluşturma  
 Bu kılavuzda kod örnekleri çoğu düğmesi denetimleri için olay işleyicileri olacak şekilde tasarlanmıştır. Aşağıdaki tabloda, kod örnekleri eşleştirmek örnek uygulama ve gerekli adları için gerekli denetimleri listeler.  
  
|Denetim|Ad|(Gerektiğinde) metin özelliği|  
|-------------|----------|---------------------------------|  
|<xref:System.Windows.Forms.Button>|`buttonEncryptFile`|Dosya şifreleme|  
|<xref:System.Windows.Forms.Button>|`buttonDecryptFile`|Dosyanın şifresini çözme|  
|<xref:System.Windows.Forms.Button>|`buttonCreateAsmKeys`|Anahtarları oluştur|  
|<xref:System.Windows.Forms.Button>|`buttonExportPublicKey`|Ortak anahtar dışarı aktarma|  
|<xref:System.Windows.Forms.Button>|`buttonImportPublicKey`|İçeri aktarma ortak anahtar|  
|<xref:System.Windows.Forms.Button>|`buttonGetPrivateKey`|Özel anahtarı alma|  
|<xref:System.Windows.Forms.Label>|`label1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog2`||  
  
 Kendi olay işleyicileri oluşturmak için Visual Studio Tasarımcısı'nda düğmeleri çift tıklayın.  
  
## <a name="declaring-global-objects"></a>Genel nesne bildirme  
 Aşağıdaki kod formun oluşturucuyu ekleyin. Ortamınız ve tercihlerinizle dize değişkenleri düzenleyin.  
  
 [!code-csharp[CryptoWalkThru#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#1)]
 [!code-vb[CryptoWalkThru#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#1)]  
  
## <a name="creating-an-asymmetric-key"></a>Asimetrik anahtar oluşturma  
 Bu görev şifreler ve şifresini çözer bir asimetrik anahtar oluşturur <xref:System.Security.Cryptography.RijndaelManaged> anahtarı. Bu anahtar, içeriği şifrelemek için kullanılan ve etiket denetimi anahtar kapsayıcı adı görüntüler.  
  
 Aşağıdaki kodu olarak ekleme `Click` için olay işleyicisini `Create Keys` düğmesi (`buttonCreateAsmKeys_Click`).  
  
 [!code-csharp[CryptoWalkThru#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#2)]
 [!code-vb[CryptoWalkThru#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#2)]  
  
## <a name="encrypting-a-file"></a>Bir dosya şifreleme  
 Bu görev, iki yöntem içerir: olay işleyicisi yöntemi için `Encrypt File` düğmesi (`buttonEncryptFile_Click`) ve `EncryptFile` yöntemi. İlk yöntem bir dosya seçmek için bir iletişim kutusu görüntüler ve dosya adını şifreleme gerçekleştirir ikinci yöntemine geçirir.  
  
 Şifrelenmiş içerik, anahtar ve IV tüm birine kaydedilir <xref:System.IO.FileStream>, adlandırılır şifreleme paketi olarak.  
  
 `EncryptFile` Yöntemi aşağıdakileri yapar:  
  
1.  Oluşturur bir <xref:System.Security.Cryptography.RijndaelManaged> içeriği şifrelemek için simetrik algoritması.  
  
2.  Oluşturur bir <xref:System.Security.Cryptography.RSACryptoServiceProvider> şifrelemek için nesne <xref:System.Security.Cryptography.RijndaelManaged> anahtarı.  
  
3.  Kullanan bir <xref:System.Security.Cryptography.CryptoStream> okuyun ve şifrelemek için nesne <xref:System.IO.FileStream> kaynak dosyasının baytlara bir hedef bloklarını <xref:System.IO.FileStream> şifrelenmiş dosya nesnesi.  
  
4.  Bayt dizileri uzunluğu değerlerine oluşturur ve IV ve şifrelenmiş anahtar uzunlukları belirler.  
  
5.  Bu anahtar, IV ve uzunluğu değerlerine şifrelenmiş paketi yazar.  
  
 Şifreleme paketi aşağıdaki biçimi kullanır:  
  
-   Anahtar uzunluğu, bayt 0 - 3  
  
-   IV uzunluğu, bayt 4-7  
  
-   Şifrelenmiş anahtar  
  
-   IV  
  
-   Şifreli metin  
  
 Başlangıç noktaları ve ardından dosyasının şifresini çözmek için kullanılan şifreleme paketinin tüm bölümlerinin uzunlukları belirlemek için IV ve anahtar uzunluklarını kullanın.  
  
 Aşağıdaki kodu olarak ekleme `Click` için olay işleyicisini `Encrypt File` düğmesi (`buttonEncryptFile_Click`).  
  
 [!code-csharp[CryptoWalkThru#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#3)]
 [!code-vb[CryptoWalkThru#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#3)]  
  
 Aşağıdakileri ekleyin `EncryptFile` forma yöntemi.  
  
 [!code-csharp[CryptoWalkThru#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#5)]
 [!code-vb[CryptoWalkThru#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#5)]  
  
## <a name="decrypting-a-file"></a>Bir dosyanın şifresini çözmek üzere  
 Bu görev, iki yöntem, olay işleyicisi yöntemini içerir `Decrypt File` düğmesi (`buttonEncryptFile_Click`) ve `DecryptFile` yöntemi. İlk yöntem, bir dosya seçmek için bir iletişim kutusu görüntüler ve şifre çözme gerçekleştiren bir ikinci yöntem dosya adıyla geçirir.  
  
 `Decrypt` Yöntemi aşağıdakileri yapar:  
  
1.  Oluşturur bir <xref:System.Security.Cryptography.RijndaelManaged> içeriğin şifresini çözmek için simetrik algoritması.  
  
2.  İlk sekiz baytı okur <xref:System.IO.FileStream> şifrelenmiş anahtar ve IV uzunluklarının edinme bayt dizileri halinde şifrelenmiş paketi.  
  
3.  Anahtar ve IV şifreleme paketinden bayt diziye ayıklar.  
  
4.  Oluşturur bir <xref:System.Security.Cryptography.RSACryptoServiceProvider> şifresini çözmek için nesne <xref:System.Security.Cryptography.RijndaelManaged> anahtarı.  
  
5.  Kullanan bir <xref:System.Security.Cryptography.CryptoStream> okuyun ve şifre metin bölümünü şifresini çözmek için nesne <xref:System.IO.FileStream> şifreleme paketini, bayt bloklarında içine <xref:System.IO.FileStream> şifresi çözülen dosya nesnesi. Bu tamamlandığında, şifre çözme tamamlandı.  
  
 Aşağıdaki kodu olarak ekleme `Click` için olay işleyicisini `Decrypt File` düğmesi.  
  
 [!code-csharp[CryptoWalkThru#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#4)]
 [!code-vb[CryptoWalkThru#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#4)]  
  
 Aşağıdakileri ekleyin `DecryptFile` forma yöntemi.  
  
 [!code-csharp[CryptoWalkThru#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#6)]
 [!code-vb[CryptoWalkThru#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#6)]  
  
## <a name="exporting-a-public-key"></a>Bir ortak anahtar dışarı aktarma  
 Bu görevi tarafından oluşturulan anahtarı kaydeder `Create Keys` bir dosyaya düğmesi. Yalnızca ortak parametreleri aktarır.  
  
 Bu görev, böylece kendisinin dosyaları her için şifreleyebilirsiniz Bob kendi ortak anahtar vermiş Alice senaryo benzetimini yapar. Kendisinin ve başkalarının ortak anahtara sahip tam anahtar çiftinin özel parametrelere sahip olmadığı için bunların şifrelerini çözmek mümkün olmaz.  
  
 Aşağıdaki kodu olarak ekleme `Click` için olay işleyicisini `Export Public Key` düğmesi (`buttonExportPublicKey_Click`).  
  
 [!code-csharp[CryptoWalkThru#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#8)]
 [!code-vb[CryptoWalkThru#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#8)]  
  
## <a name="importing-a-public-key"></a>Bir ortak anahtar alma  
 Bu görevi yalnızca ortak parametreleriyle anahtar tarafından oluşturulan gibi yükler `Export Public Key` düğmesine tıklayın ve anahtar kapsayıcı adı olarak ayarlar.  
  
 Bu görev, kendisinin dosyaları her için şifreleyebilirsiniz şekilde yalnızca ortak parametreleri Alice'in anahtarla yüklenirken Bob senaryo benzetimini yapar.  
  
 Aşağıdaki kodu olarak ekleme `Click` için olay işleyicisini `Import Public Key` düğmesi (`buttonImportPublicKey_Click`).  
  
 [!code-csharp[CryptoWalkThru#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#9)]
 [!code-vb[CryptoWalkThru#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#9)]  
  
## <a name="getting-a-private-key"></a>Bir özel anahtar alma  
 Bu görev, anahtar kapsayıcı adı kullanılarak oluşturulan anahtarın adını ayarlar `Create Keys` düğmesi. Anahtar kapsayıcısı özel parametrelerle tam anahtar çifti içerir.  
  
 Bu görev Bob tarafından şifrelenmiş dosyaların şifresini çözmek için kendi özel anahtarı kullanarak Alice senaryo benzetimini yapar.  
  
 Aşağıdaki kodu olarak ekleme `Click` için olay işleyicisini `Get Private Key` düğmesi (`buttonGetPrivateKey_Click`).  
  
 [!code-csharp[CryptoWalkThru#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#7)]
 [!code-vb[CryptoWalkThru#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#7)]  
  
## <a name="testing-the-application"></a>Uygulamayı Test Etme  
 Uygulamayı oluşturduktan sonra aşağıdaki test senaryolarını gerçekleştirin.  
  
#### <a name="to-create-keys-encrypt-and-decrypt"></a>Anahtarlar oluşturmak, şifrelemek ve şifresini çözmek için  
  
1.  Tıklatın `Create Keys` düğmesi. Etiket anahtarı adını görüntüler ve tam anahtar çifti olduğunu gösterir.  
  
2.  Tıklatın `Export Public Key` düğmesi. Ortak anahtar parametreleri dışarı aktarma geçerli anahtar değiştirmez unutmayın.  
  
3.  Tıklatın `Encrypt File` düğmesine tıklayın ve bir dosya seçin.  
  
4.  Tıklatın `Decrypt File` düğmesini tıklatın ve yalnızca şifrelenmiş dosya seçin.  
  
5.  Yalnızca şifresi dosyasını inceleyin.  
  
6.  Uygulamayı kapatın ve İleri senaryosunda test alınırken kalıcı anahtar kapsayıcıları için yeniden başlatın.  
  
#### <a name="to-encrypt-using-the-public-key"></a>Ortak anahtar kullanarak şifrelemek için  
  
1.  Tıklatın `Import Public Key` düğmesi. Etiket anahtar adını görüntüler ve bunun yalnızca ortak olduğunu gösterir.  
  
2.  Tıklatın `Encrypt File` düğmesine tıklayın ve bir dosya seçin.  
  
3.  Tıklatın `Decrypt File` düğmesini tıklatın ve yalnızca şifrelenmiş dosya seçin. Özel anahtarın şifresini olması gerektiği için bu başarısız olur.  
  
 Bu senaryo için başka bir kişi bir dosyayı şifrelemek için yalnızca ortak anahtarın gösterir. Genellikle bu kişi yalnızca ortak anahtar verin ve bu şifre çözme için özel anahtar stopajdan.  
  
#### <a name="to-decrypt-using-the-private-key"></a>Özel anahtarı kullanarak şifresini çözmek için  
  
1.  Tıklatın `Get Private Key` düğmesi. Etiket anahtarı adını görüntüler ve tam anahtar çifti olup olmadığını gösterir.  
  
2.  Tıklatın `Decrypt File` düğmesini tıklatın ve yalnızca şifrelenmiş dosya seçin. Şifresini çözmek için tam anahtar çifti olduğundan bu başarılı olacaktır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md)
