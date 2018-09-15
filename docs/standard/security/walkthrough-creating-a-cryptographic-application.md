---
title: 'İzlenecek Yol: Şifreleme Uygulaması Oluşturma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [NET Framework], example
- cryptography [NET Framework], cryptographic application example
- cryptography [NET Framework], application example
ms.assetid: abf48c11-1e72-431d-9562-39cf23e1a8ff
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 873b6120929c8c7cf67d53d8f793964361ae88b8
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2018
ms.locfileid: "45649496"
---
# <a name="walkthrough-creating-a-cryptographic-application"></a>İzlenecek Yol: Şifreleme Uygulaması Oluşturma
Bu izlenecek yol, şifrelemek ve içeriğin şifresini gösterilmektedir. Kod örnekleri, bir Windows Forms uygulaması için tasarlanmıştır. Bu uygulama, akıllı kart kullanma gibi gerçek dünya senaryolarını göstermemiz gerekmez. Bunun yerine, şifreleme ve şifre çözme temellerini gösterir.  
  
 Bu izlenecek yol aşağıdaki yönergeler için şifreleme kullanır:  
  
-   Kullanım <xref:System.Security.Cryptography.RijndaelManaged> sınıfı, şifrelemek ve kendi otomatik olarak oluşturulan kullanarak verilerin şifresini bir Simetrik algoritma <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> ve <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>.  
  
-   Kullanım <xref:System.Security.Cryptography.RSACryptoServiceProvider>, şifreleme ve anahtar tarafından şifrelenmiş verilerin şifresini çözmek için bir asimetrik algoritma <xref:System.Security.Cryptography.RijndaelManaged>. Asimetrik algoritmalar, daha küçük miktarda bir anahtarı gibi veriler için en iyi şekilde kullanılır.  
  
    > [!NOTE]
    >  Şifrelenmiş içeriği diğer kullanıcılarla değişimi yerine bilgisayarınızdaki verileri korumak istiyorsanız, kullanmayı <xref:System.Security.Cryptography.ProtectedData> veya <xref:System.Security.Cryptography.ProtectedMemory> sınıfları.  
  
 Aşağıdaki tabloda, bu konudaki şifreleme görevleri özetler.  
  
|Görev|Açıklama|  
|----------|-----------------|  
|Bir Windows Forms uygulaması oluşturma|Uygulamayı çalıştırmak için gerekli denetimleri listeler.|  
|Genel nesne bildirme|Yol değişkenleri, dize bildirir <xref:System.Security.Cryptography.CspParameters>ve <xref:System.Security.Cryptography.RSACryptoServiceProvider> genel kapsamında sahip <xref:System.Windows.Forms.Form> sınıfı.|  
|Asimetrik anahtar oluşturma|Bir asimetrik ortak ve özel anahtar değer çifti oluşturur ve bir anahtar kapsayıcısı adını atar.|  
|Bir dosya şifreleme|Şifreleme için bir dosya seçmek için bir iletişim kutusu görüntüler ve dosyayı şifreler.|  
|Bir dosyanın şifresini çözmek üzere|Şifre çözme için şifrelenmiş bir dosya seçmek için bir iletişim kutusu görüntüler ve dosyanın şifresini çözer.|  
|Özel anahtarı alma|Tam anahtar çiftini kullanarak anahtar kapsayıcısı adını alır.|  
|Ortak anahtarı dışarı aktarma|Bu anahtar yalnızca ortak parametreleri içeren bir XML dosyası kaydeder.|  
|Bir ortak anahtar içeri aktarma|Anahtarı bir XML dosyasından anahtar kapsayıcısına yükler.|  
|Uygulamayı test etme|Bu uygulamayı test etme yordamları listeler.|  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   Başvurular <xref:System.IO> ve <xref:System.Security.Cryptography> ad alanları.  
  
## <a name="creating-a-windows-forms-application"></a>Bir Windows Forms uygulaması oluşturma  
 Bu izlenecek yolda kod örnekleri çoğu, düğme denetimleri için olay işleyicileri olacak şekilde tasarlanmıştır. Aşağıdaki tablo kod örneklerle eşleşmesi örnek uygulamayı ve gerekli adları için gerekli denetimleri listeler.  
  
|Denetim|Ad|Metin özelliği (gereken şekilde)|  
|-------------|----------|---------------------------------|  
|<xref:System.Windows.Forms.Button>|`buttonEncryptFile`|Dosya şifreleme|  
|<xref:System.Windows.Forms.Button>|`buttonDecryptFile`|Dosyasının şifresini çözme|  
|<xref:System.Windows.Forms.Button>|`buttonCreateAsmKeys`|Anahtarları oluşturma|  
|<xref:System.Windows.Forms.Button>|`buttonExportPublicKey`|Ortak anahtarı dışarı aktar|  
|<xref:System.Windows.Forms.Button>|`buttonImportPublicKey`|Ortak anahtar içeri aktarma|  
|<xref:System.Windows.Forms.Button>|`buttonGetPrivateKey`|Özel anahtarı alma|  
|<xref:System.Windows.Forms.Label>|`label1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog2`||  
  
 Olay işleyicilerini oluşturmak için Visual Studio Tasarımcısı'nda düğmeleri çift tıklayın.  
  
## <a name="declaring-global-objects"></a>Genel nesne bildirme  
 Aşağıdaki kod, formun oluşturucuyu ekleyin. Dize değişkenleri ortamınız ve tercihlerinizle düzenleyin.  
  
 [!code-csharp[CryptoWalkThru#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#1)]
 [!code-vb[CryptoWalkThru#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#1)]  
  
## <a name="creating-an-asymmetric-key"></a>Asimetrik anahtar oluşturma  
 Bu görev, şifreler ve şifresini çözer asimetrik bir anahtar oluşturur. <xref:System.Security.Cryptography.RijndaelManaged> anahtarı. Bu anahtar, içeriği şifrelemek için kullanılan ve etiket denetiminde anahtar kapsayıcısı adını görüntüler.  
  
 Aşağıdaki kodu olarak ekleyin `Click` için olay işleyicisi `Create Keys` düğmesine (`buttonCreateAsmKeys_Click`).  
  
 [!code-csharp[CryptoWalkThru#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#2)]
 [!code-vb[CryptoWalkThru#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#2)]  
  
## <a name="encrypting-a-file"></a>Bir dosya şifreleme  
 Bu görev, iki yöntem içerir: olay işleyicisi yöntemi için `Encrypt File` düğmesine (`buttonEncryptFile_Click`) ve `EncryptFile` yöntemi. İlk yöntem, bir dosya seçmek için bir iletişim kutusu görüntüler ve dosya adını şifreleme gerçekleştirir ikinci yöntem geçirir.  
  
 Şifrelenmiş içeriği, anahtar ve IV tümü için kaydedilir <xref:System.IO.FileStream>, adlandırılır şifreleme paketi olarak.  
  
 `EncryptFile` Yöntemi şunları yapar:  
  
1.  Oluşturur bir <xref:System.Security.Cryptography.RijndaelManaged> içeriği şifrelemek için Simetrik algoritma.  
  
2.  Oluşturur bir <xref:System.Security.Cryptography.RSACryptoServiceProvider> şifrelemek için nesne <xref:System.Security.Cryptography.RijndaelManaged> anahtarı.  
  
3.  Kullanan bir <xref:System.Security.Cryptography.CryptoStream> okuyun ve şifrelemek üzere nesne <xref:System.IO.FileStream> baytlara hedef blokları kaynak dosyasının <xref:System.IO.FileStream> şifrelenmiş dosya için nesne.  
  
4.  Şifrelenmiş anahtarı ve IV'yi uzunluklarının belirler ve uzunluğu değerlerine bayt dizileri oluşturur.  
  
5.  Anahtar ve IV uzunluğu değerlerine şifrelenmiş paketi yazar.  
  
 Şifreleme paketi aşağıdaki biçimdedir:  
  
-   Anahtar uzunluğu, bayt 0 - 3  
  
-   IV uzunluğu, 4-7 bayt  
  
-   Şifrelenmiş anahtarı  
  
-   IV  
  
-   Şifre metni  
  
 Anahtar ve IV uzunluklarının başlangıç noktaları ve ardından dosyasının şifresini çözmek için kullanılan şifreleme paketinin tüm bölümlerinin uzunlukları belirlemek için kullanabilirsiniz.  
  
 Aşağıdaki kodu olarak ekleyin `Click` için olay işleyicisi `Encrypt File` düğmesine (`buttonEncryptFile_Click`).  
  
 [!code-csharp[CryptoWalkThru#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#3)]
 [!code-vb[CryptoWalkThru#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#3)]  
  
 Aşağıdaki `EncryptFile` forma yöntemi.  
  
 [!code-csharp[CryptoWalkThru#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#5)]
 [!code-vb[CryptoWalkThru#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#5)]  
  
## <a name="decrypting-a-file"></a>Bir dosyanın şifresini çözmek üzere  
 Bu görev, olay işleyicisi yöntemi için iki yöntemi içerir. `Decrypt File` düğmesine (`buttonDecryptFile_Click`) ve `DecryptFile` yöntemi. İlk yöntem, bir dosya seçmek için bir iletişim kutusu görüntüler ve şifre çözme gerçekleştiren bir ikinci yöntem dosyası adını geçirir.  
  
 `Decrypt` Yöntemi şunları yapar:  
  
1.  Oluşturur bir <xref:System.Security.Cryptography.RijndaelManaged> içeriğin şifresini Simetrik algoritma.  
  
2.  İlk sekiz baytı okur <xref:System.IO.FileStream> şifrelenmiş anahtar ve IV uzunluklarının alınacağı bayt dizileri halinde şifrelenmiş paketi.  
  
3.  Anahtar ve IV şifreleme paketinden bayt dizileri ayıklar.  
  
4.  Oluşturur bir <xref:System.Security.Cryptography.RSACryptoServiceProvider> şifresini çözmek için nesne <xref:System.Security.Cryptography.RijndaelManaged> anahtarı.  
  
5.  Kullanan bir <xref:System.Security.Cryptography.CryptoStream> okuyun ve şifre metin bölümünü şifresini çözmek için nesne <xref:System.IO.FileStream> şifreleme paketlemeden, bayt cinsinden bloklarında <xref:System.IO.FileStream> şifresi çözülen dosya için nesne. Bu tamamlandığında, şifre çözme tamamlanır.  
  
 Aşağıdaki kodu olarak ekleyin `Click` için olay işleyicisi `Decrypt File` düğmesi.  
  
 [!code-csharp[CryptoWalkThru#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#4)]
 [!code-vb[CryptoWalkThru#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#4)]  
  
 Aşağıdaki `DecryptFile` forma yöntemi.  
  
 [!code-csharp[CryptoWalkThru#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#6)]
 [!code-vb[CryptoWalkThru#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#6)]  
  
## <a name="exporting-a-public-key"></a>Ortak anahtarı dışarı aktarma  
 Bu görev tarafından oluşturulan anahtarı kaydeder `Create Keys` dosyaya düğmesi. Bunu yalnızca ortak parametreleri aktarır.  
  
 Bu görevi, böylece o dosyaları için her şifreleyebilirsiniz Bob kendi ortak anahtar verme Alice senaryo benzetimini yapar. He ve ilgili ortak anahtara sahip diğer özel parametreler tam anahtar çiftiyle olmadığı için bunların şifresini çözmek mümkün olmayacaktır.  
  
 Aşağıdaki kodu olarak ekleyin `Click` için olay işleyicisi `Export Public Key` düğmesine (`buttonExportPublicKey_Click`).  
  
 [!code-csharp[CryptoWalkThru#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#8)]
 [!code-vb[CryptoWalkThru#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#8)]  
  
## <a name="importing-a-public-key"></a>Bir ortak anahtar içeri aktarma  
 Bu görev tarafından oluşturulan anahtar yalnızca ortak parametreleriyle yükler `Export Public Key` düğmesini ve anahtar kapsayıcısı adını ayarlar.  
  
 Bu görevi, Alice'in anahtar yalnızca ortak parametreleri ile yaptığı dosyaları için her şifreleyebilirsiniz şekilde yükleniyor Bob senaryo benzetimini yapar.  
  
 Aşağıdaki kodu olarak ekleyin `Click` için olay işleyicisi `Import Public Key` düğmesine (`buttonImportPublicKey_Click`).  
  
 [!code-csharp[CryptoWalkThru#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#9)]
 [!code-vb[CryptoWalkThru#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#9)]  
  
## <a name="getting-a-private-key"></a>Bir özel anahtar alma  
 Bu görevi kullanılarak oluşturulan anahtarın adını anahtar kapsayıcısı adını ayarlar `Create Keys` düğmesi. Anahtar kapsayıcısı tam anahtar çiftinin özel parametrelerle içerir.  
  
 Bu görev Alice, Bob tarafından şifrelenmiş dosyaların şifresini çözmek için kendi özel anahtarı kullanarak bir senaryo benzetimini yapar.  
  
 Aşağıdaki kodu olarak ekleyin `Click` için olay işleyicisi `Get Private Key` düğmesine (`buttonGetPrivateKey_Click`).  
  
 [!code-csharp[CryptoWalkThru#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#7)]
 [!code-vb[CryptoWalkThru#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#7)]  
  
## <a name="testing-the-application"></a>Uygulamayı Test Etme  
 Uygulamayı oluşturduktan sonra aşağıdaki test senaryoları gerçekleştirin.  
  
#### <a name="to-create-keys-encrypt-and-decrypt"></a>Anahtarları oluşturmak için şifrelemek ve şifresini çözme  
  
1.  Tıklayın `Create Keys` düğmesi. Etiket anahtarı adını görüntüler ve tam anahtar çifti olduğunu gösterir.  
  
2.  Tıklayın `Export Public Key` düğmesi. Ortak anahtar parametreleri verme geçerli anahtar değiştirmez unutmayın.  
  
3.  Tıklayın `Encrypt File` düğmesine tıklayın ve bir dosya seçin.  
  
4.  Tıklayın `Decrypt File` düğmesine tıklayın ve yalnızca şifrelenmiş dosya belirleyin.  
  
5.  Yalnızca şifresi dosyasını inceleyin.  
  
6.  Uygulamayı kapatın ve alınırken kalıcı anahtar kapsayıcıları bir sonraki senaryoda test etmek için yeniden başlatın.  
  
#### <a name="to-encrypt-using-the-public-key"></a>Ortak anahtar kullanarak şifrelemek için  
  
1.  Tıklayın `Import Public Key` düğmesi. Etiket, anahtar adını görüntüler ve bunun yalnızca genel olduğunu gösterir.  
  
2.  Tıklayın `Encrypt File` düğmesine tıklayın ve bir dosya seçin.  
  
3.  Tıklayın `Decrypt File` düğmesine tıklayın ve yalnızca şifrelenmiş dosya belirleyin. Özel anahtarın şifresini çözmek için sahip olması gerektiğinden bu başarısız olur.  
  
 Bu senaryo, bir dosyayı başka bir kişi için şifrelemek için yalnızca ortak anahtarın gösterir. Genellikle söz konusu kişinin, size yalnızca ortak anahtar ve şifre çözme için özel anahtarın stopaj.  
  
#### <a name="to-decrypt-using-the-private-key"></a>Özel anahtarı kullanarak şifresini çözmek için  
  
1.  Tıklayın `Get Private Key` düğmesi. Etiket anahtarı adını görüntüler ve tam bir anahtar çifti olup olmadığını gösterir.  
  
2.  Tıklayın `Decrypt File` düğmesine tıklayın ve yalnızca şifrelenmiş dosya belirleyin. Tam anahtar çifti şifresini çözmek için sahip olduğunuz için bu başarılı olacaktır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md)
