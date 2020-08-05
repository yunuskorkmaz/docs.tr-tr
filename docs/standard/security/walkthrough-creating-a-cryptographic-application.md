---
title: 'İzlenecek yol: Şifreleme Uygulaması Oluşturma'
description: Bir şifreleme uygulamasının oluşturulmasına yol gösterir. Windows Forms uygulamasındaki içeriği şifrelemeyi ve şifrelerini çözmeyi öğrenin.
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [NET], example
- cryptography [NET], cryptographic application example
- cryptography [NET], application example
ms.assetid: abf48c11-1e72-431d-9562-39cf23e1a8ff
ms.openlocfilehash: 16a887f23c584daa83106ae61c497bcae8dc4dd2
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557196"
---
# <a name="walkthrough-creating-a-cryptographic-application"></a><span data-ttu-id="325d5-104">İzlenecek yol: Şifreleme Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="325d5-104">Walkthrough: Creating a Cryptographic Application</span></span>

> [!NOTE]
> <span data-ttu-id="325d5-105">Bu makale Windows için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="325d5-105">This article applies to Windows.</span></span>
>
> <span data-ttu-id="325d5-106">ASP.NET Core hakkında bilgi için bkz. [ASP.NET Core Data Protection](/aspnet/core/security/data-protection/introduction).</span><span class="sxs-lookup"><span data-stu-id="325d5-106">For information about ASP.NET Core, see [ASP.NET Core Data Protection](/aspnet/core/security/data-protection/introduction).</span></span>

<span data-ttu-id="325d5-107">Bu izlenecek yol, içerik şifrelemesini ve şifresini çözmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="325d5-107">This walkthrough demonstrates how to encrypt and decrypt content.</span></span> <span data-ttu-id="325d5-108">Kod örnekleri, Windows Forms bir uygulama için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="325d5-108">The code examples are designed for a Windows Forms application.</span></span> <span data-ttu-id="325d5-109">Bu uygulama, akıllı kartlar kullanma gibi gerçek dünyada senaryolar göstermez.</span><span class="sxs-lookup"><span data-stu-id="325d5-109">This application does not demonstrate real world scenarios, such as using smart cards.</span></span> <span data-ttu-id="325d5-110">Bunun yerine, şifreleme ve şifre çözme temellerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="325d5-110">Instead, it demonstrates the fundamentals of encryption and decryption.</span></span>  
  
<span data-ttu-id="325d5-111">Bu izlenecek yol, şifreleme için aşağıdaki yönergeleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="325d5-111">This walkthrough uses the following guidelines for encryption:</span></span>  
  
- <span data-ttu-id="325d5-112"><xref:System.Security.Cryptography.Aes>Otomatik olarak oluşturulan ve kullanarak verileri şifrelemek ve şifrelerini çözmek için simetrik bir algoritma sınıfını kullanın <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A> .</span><span class="sxs-lookup"><span data-stu-id="325d5-112">Use the <xref:System.Security.Cryptography.Aes> class, a symmetric algorithm, to encrypt and decrypt data by using its automatically generated <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> and <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>.</span></span>  
  
- <span data-ttu-id="325d5-113"><xref:System.Security.Cryptography.RSA>Tarafından şifrelenen verilerle anahtarı şifrelemek ve şifresini çözmek için asimetrik algoritmayı kullanın <xref:System.Security.Cryptography.Aes> .</span><span class="sxs-lookup"><span data-stu-id="325d5-113">Use the <xref:System.Security.Cryptography.RSA> asymmetric algorithm to encrypt and decrypt the key to the data encrypted by <xref:System.Security.Cryptography.Aes>.</span></span> <span data-ttu-id="325d5-114">Asimetrik algoritmalar, anahtar gibi daha küçük miktarlarda veri için en iyi şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="325d5-114">Asymmetric algorithms are best used for smaller amounts of data, such as a key.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="325d5-115">Diğer kişilerle şifrelenmiş içerik değişimi yerine bilgisayarınızdaki verileri korumak istiyorsanız, sınıfını kullanmayı düşünün <xref:System.Security.Cryptography.ProtectedData> .</span><span class="sxs-lookup"><span data-stu-id="325d5-115">If you want to protect data on your computer instead of exchanging encrypted content with other people, consider using the <xref:System.Security.Cryptography.ProtectedData> class.</span></span>  
  
 <span data-ttu-id="325d5-116">Aşağıdaki tabloda bu konudaki şifreleme görevleri özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="325d5-116">The following table summarizes the cryptographic tasks in this topic.</span></span>  
  
|<span data-ttu-id="325d5-117">Görev</span><span class="sxs-lookup"><span data-stu-id="325d5-117">Task</span></span>|<span data-ttu-id="325d5-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="325d5-118">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="325d5-119">Windows Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="325d5-119">Creating a Windows Forms application</span></span>|<span data-ttu-id="325d5-120">Uygulamayı çalıştırmak için gereken denetimleri listeler.</span><span class="sxs-lookup"><span data-stu-id="325d5-120">Lists the controls that are required to run the application.</span></span>|  
|<span data-ttu-id="325d5-121">Genel nesneleri bildirme</span><span class="sxs-lookup"><span data-stu-id="325d5-121">Declaring global objects</span></span>|<span data-ttu-id="325d5-122">Dize yol değişkenlerini, <xref:System.Security.Cryptography.CspParameters> ve ' ı <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfının genel bağlamına sahip olacak şekilde bildirir <xref:System.Windows.Forms.Form> .</span><span class="sxs-lookup"><span data-stu-id="325d5-122">Declares string path variables, the <xref:System.Security.Cryptography.CspParameters>, and the <xref:System.Security.Cryptography.RSACryptoServiceProvider> to have global context of the <xref:System.Windows.Forms.Form> class.</span></span>|  
|<span data-ttu-id="325d5-123">Asimetrik anahtar oluşturma</span><span class="sxs-lookup"><span data-stu-id="325d5-123">Creating an asymmetric key</span></span>|<span data-ttu-id="325d5-124">Asimetrik ortak ve özel anahtar değer çifti oluşturur ve bir anahtar kapsayıcısı adı atar.</span><span class="sxs-lookup"><span data-stu-id="325d5-124">Creates an asymmetric public and private key value pair and assigns it a key container name.</span></span>|  
|<span data-ttu-id="325d5-125">Dosya şifreleme</span><span class="sxs-lookup"><span data-stu-id="325d5-125">Encrypting a file</span></span>|<span data-ttu-id="325d5-126">Şifreleme için bir dosya seçmek üzere bir iletişim kutusu görüntüler ve dosyayı şifreler.</span><span class="sxs-lookup"><span data-stu-id="325d5-126">Displays a dialog box to select a file for encryption and encrypts the file.</span></span>|  
|<span data-ttu-id="325d5-127">Dosya şifresini çözme</span><span class="sxs-lookup"><span data-stu-id="325d5-127">Decrypting a file</span></span>|<span data-ttu-id="325d5-128">Şifre çözme için şifrelenmiş bir dosya seçmek ve dosyanın şifresini çözmek için bir iletişim kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="325d5-128">Displays a dialog box to select an encrypted file for decryption and decrypts the file.</span></span>|  
|<span data-ttu-id="325d5-129">Özel anahtar alma</span><span class="sxs-lookup"><span data-stu-id="325d5-129">Getting a private key</span></span>|<span data-ttu-id="325d5-130">Anahtar kapsayıcısı adını kullanarak tam anahtar çiftini alır.</span><span class="sxs-lookup"><span data-stu-id="325d5-130">Gets the full key pair using the key container name.</span></span>|  
|<span data-ttu-id="325d5-131">Ortak anahtar dışarı aktarılıyor</span><span class="sxs-lookup"><span data-stu-id="325d5-131">Exporting a public key</span></span>|<span data-ttu-id="325d5-132">Anahtarı yalnızca ortak parametrelere sahip bir XML dosyasına kaydeder.</span><span class="sxs-lookup"><span data-stu-id="325d5-132">Saves the key to an XML file with only public parameters.</span></span>|  
|<span data-ttu-id="325d5-133">Ortak anahtar içeri aktarılıyor</span><span class="sxs-lookup"><span data-stu-id="325d5-133">Importing a public key</span></span>|<span data-ttu-id="325d5-134">Anahtarı bir XML dosyasından anahtar kapsayıcısına yükler.</span><span class="sxs-lookup"><span data-stu-id="325d5-134">Loads the key from an XML file into the key container.</span></span>|  
|<span data-ttu-id="325d5-135">Uygulamayı test etme</span><span class="sxs-lookup"><span data-stu-id="325d5-135">Testing the application</span></span>|<span data-ttu-id="325d5-136">Bu uygulamayı test etmek için yordamları listeler.</span><span class="sxs-lookup"><span data-stu-id="325d5-136">Lists procedures for testing this application.</span></span>|  
  
## <a name="prerequisites"></a><span data-ttu-id="325d5-137">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="325d5-137">Prerequisites</span></span>  

<span data-ttu-id="325d5-138">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="325d5-138">You need the following components to complete this walkthrough:</span></span>  
  
- <span data-ttu-id="325d5-139"><xref:System.IO>Ve <xref:System.Security.Cryptography> ad alanlarına başvurular.</span><span class="sxs-lookup"><span data-stu-id="325d5-139">References to the <xref:System.IO> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
## <a name="creating-a-windows-forms-application"></a><span data-ttu-id="325d5-140">Windows Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="325d5-140">Creating a Windows Forms Application</span></span>  

<span data-ttu-id="325d5-141">Bu izlenecek yolda bulunan kod örneklerinin çoğu düğme denetimleri için olay işleyicileri olacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="325d5-141">Most of the code examples in this walkthrough are designed to be event handlers for button controls.</span></span> <span data-ttu-id="325d5-142">Aşağıdaki tabloda, örnek uygulama için gereken denetimler ve kod örnekleriyle eşleşmesi için gereken adlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="325d5-142">The following table lists the controls required for the sample application and their required names to match the code examples.</span></span>  
  
|<span data-ttu-id="325d5-143">Denetim</span><span class="sxs-lookup"><span data-stu-id="325d5-143">Control</span></span>|<span data-ttu-id="325d5-144">Ad</span><span class="sxs-lookup"><span data-stu-id="325d5-144">Name</span></span>|<span data-ttu-id="325d5-145">Metin özelliği (gerektiğinde)</span><span class="sxs-lookup"><span data-stu-id="325d5-145">Text property (as needed)</span></span>|  
|-------------|----------|---------------------------------|  
|<xref:System.Windows.Forms.Button>|`buttonEncryptFile`|<span data-ttu-id="325d5-146">Dosyayı şifreleyin</span><span class="sxs-lookup"><span data-stu-id="325d5-146">Encrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonDecryptFile`|<span data-ttu-id="325d5-147">Dosya şifresini çöz</span><span class="sxs-lookup"><span data-stu-id="325d5-147">Decrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonCreateAsmKeys`|<span data-ttu-id="325d5-148">Anahtar oluştur</span><span class="sxs-lookup"><span data-stu-id="325d5-148">Create Keys</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonExportPublicKey`|<span data-ttu-id="325d5-149">Ortak anahtarı dışarı aktar</span><span class="sxs-lookup"><span data-stu-id="325d5-149">Export Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonImportPublicKey`|<span data-ttu-id="325d5-150">Ortak anahtarı içeri aktar</span><span class="sxs-lookup"><span data-stu-id="325d5-150">Import Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonGetPrivateKey`|<span data-ttu-id="325d5-151">Özel anahtar al</span><span class="sxs-lookup"><span data-stu-id="325d5-151">Get Private Key</span></span>|  
|<xref:System.Windows.Forms.Label>|`label1`|<span data-ttu-id="325d5-152">Anahtar ayarlanmadı</span><span class="sxs-lookup"><span data-stu-id="325d5-152">Key not set</span></span>|  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog2`||  
  
 <span data-ttu-id="325d5-153">Olay işleyicilerini oluşturmak için Visual Studio tasarımcısında düğmelere çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="325d5-153">Double-click the buttons in the Visual Studio designer to create their event handlers.</span></span>
  
## <a name="declaring-global-objects"></a><span data-ttu-id="325d5-154">Genel nesneleri bildirme</span><span class="sxs-lookup"><span data-stu-id="325d5-154">Declaring Global Objects</span></span>  

<span data-ttu-id="325d5-155">Form yapıcısına aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="325d5-155">Add the following code to the Form's constructor.</span></span> <span data-ttu-id="325d5-156">Ortamınız ve tercihleriniz için dize değişkenlerini düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="325d5-156">Edit the string variables for your environment and preferences.</span></span>  
  
[!code-csharp[CryptoWalkThru#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#1)]
[!code-vb[CryptoWalkThru#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#1)]  
  
## <a name="creating-an-asymmetric-key"></a><span data-ttu-id="325d5-157">Asimetrik anahtar oluşturma</span><span class="sxs-lookup"><span data-stu-id="325d5-157">Creating an Asymmetric Key</span></span>  

<span data-ttu-id="325d5-158">Bu görev, anahtarı şifreleyen ve şifresini çözdüğü bir asimetrik anahtar oluşturur <xref:System.Security.Cryptography.Aes> .</span><span class="sxs-lookup"><span data-stu-id="325d5-158">This task creates an asymmetric key that encrypts and decrypts the <xref:System.Security.Cryptography.Aes> key.</span></span> <span data-ttu-id="325d5-159">Bu anahtar, içeriği şifrelemek için kullanıldı ve etiket denetimindeki anahtar kapsayıcısı adını görüntülüyor.</span><span class="sxs-lookup"><span data-stu-id="325d5-159">This key was used to encrypt the content and it displays the key container name on the label control.</span></span>  
  
 <span data-ttu-id="325d5-160">`Click`Düğme () için olay işleyicisi olarak aşağıdaki kodu ekleyin `Create Keys` `buttonCreateAsmKeys_Click` .</span><span class="sxs-lookup"><span data-stu-id="325d5-160">Add the following code as the `Click` event handler for the `Create Keys` button (`buttonCreateAsmKeys_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#2)]
 [!code-vb[CryptoWalkThru#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#2)]  
  
## <a name="encrypting-a-file"></a><span data-ttu-id="325d5-161">Dosya şifreleme</span><span class="sxs-lookup"><span data-stu-id="325d5-161">Encrypting a File</span></span>  

<span data-ttu-id="325d5-162">Bu görev iki yöntem içerir: `Encrypt File` Button ( `buttonEncryptFile_Click` ) ve yöntemi için olay işleyicisi yöntemi `EncryptFile` .</span><span class="sxs-lookup"><span data-stu-id="325d5-162">This task involves two methods: the event handler method for the `Encrypt File` button (`buttonEncryptFile_Click`) and the `EncryptFile` method.</span></span> <span data-ttu-id="325d5-163">İlk yöntem, bir dosya seçmek için bir iletişim kutusu görüntüler ve dosya adını şifrelemeyi gerçekleştiren ikinci yönteme geçirir.</span><span class="sxs-lookup"><span data-stu-id="325d5-163">The first method displays a dialog box for selecting a file and passes the file name to the second method, which performs the encryption.</span></span>  
  
<span data-ttu-id="325d5-164">Şifrelenmiş içerik, anahtar ve IV, <xref:System.IO.FileStream> şifreleme paketi olarak adlandırılan tek bir öğesine kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="325d5-164">The encrypted content, key, and IV are all saved to one <xref:System.IO.FileStream>, which is referred to as the encryption package.</span></span>  
  
<span data-ttu-id="325d5-165">`EncryptFile`Yöntemi aşağıdakileri yapar:</span><span class="sxs-lookup"><span data-stu-id="325d5-165">The `EncryptFile` method does the following:</span></span>  
  
1. <span data-ttu-id="325d5-166"><xref:System.Security.Cryptography.Aes>İçeriği şifrelemek için simetrik bir algoritma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="325d5-166">Creates a <xref:System.Security.Cryptography.Aes> symmetric algorithm to encrypt the content.</span></span>  
  
2. <span data-ttu-id="325d5-167"><xref:System.Security.Cryptography.RSACryptoServiceProvider>Anahtarı şifrelemek için bir nesne oluşturur <xref:System.Security.Cryptography.Aes> .</span><span class="sxs-lookup"><span data-stu-id="325d5-167">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to encrypt the <xref:System.Security.Cryptography.Aes> key.</span></span>  
  
3. <span data-ttu-id="325d5-168">, <xref:System.Security.Cryptography.CryptoStream> <xref:System.IO.FileStream> Kaynak dosyayı, bayt blokları içinde, şifrelenen dosya için bir hedef nesneye okumak ve şifrelemek için bir nesne kullanır <xref:System.IO.FileStream> .</span><span class="sxs-lookup"><span data-stu-id="325d5-168">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and encrypt the <xref:System.IO.FileStream> of the source file, in blocks of bytes, into a destination <xref:System.IO.FileStream> object for the encrypted file.</span></span>  
  
4. <span data-ttu-id="325d5-169">Şifrelenmiş anahtarın ve IV 'nin uzunluklarının sayısını belirler ve uzunluk değerlerinin bayt dizilerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="325d5-169">Determines the lengths of the encrypted key and IV, and creates byte arrays of their length values.</span></span>  
  
5. <span data-ttu-id="325d5-170">Anahtarı, IV ve bunların uzunluk değerlerini şifreli pakete yazar.</span><span class="sxs-lookup"><span data-stu-id="325d5-170">Writes the Key, IV, and their length values to the encrypted package.</span></span>  
  
 <span data-ttu-id="325d5-171">Şifreleme paketi aşağıdaki biçimi kullanır:</span><span class="sxs-lookup"><span data-stu-id="325d5-171">The encryption package uses the following format:</span></span>  
  
- <span data-ttu-id="325d5-172">Anahtar uzunluğu, bayt 0-3</span><span class="sxs-lookup"><span data-stu-id="325d5-172">Key length, bytes 0 - 3</span></span>  
  
- <span data-ttu-id="325d5-173">IV uzunluğu, bayt 4-7</span><span class="sxs-lookup"><span data-stu-id="325d5-173">IV length, bytes 4 - 7</span></span>  
  
- <span data-ttu-id="325d5-174">Şifrelenmiş anahtar</span><span class="sxs-lookup"><span data-stu-id="325d5-174">Encrypted key</span></span>  
  
- <span data-ttu-id="325d5-175">IV</span><span class="sxs-lookup"><span data-stu-id="325d5-175">IV</span></span>  
  
- <span data-ttu-id="325d5-176">Şifre metni</span><span class="sxs-lookup"><span data-stu-id="325d5-176">Cipher text</span></span>  
  
 <span data-ttu-id="325d5-177">Daha sonra dosyanın şifresini çözmek için kullanılabilecek, şifreleme paketinin tüm bölümlerinin başlangıç noktalarını ve uzunluklarının belirlenmesi için anahtar ve IV uzunluğunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="325d5-177">You can use the lengths of the key and IV to determine the starting points and lengths of all parts of the encryption package, which can then be used to decrypt the file.</span></span>  
  
 <span data-ttu-id="325d5-178">`Click`Düğme () için olay işleyicisi olarak aşağıdaki kodu ekleyin `Encrypt File` `buttonEncryptFile_Click` .</span><span class="sxs-lookup"><span data-stu-id="325d5-178">Add the following code as the `Click` event handler for the `Encrypt File` button (`buttonEncryptFile_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#3)]
 [!code-vb[CryptoWalkThru#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#3)]  
  
 <span data-ttu-id="325d5-179">Aşağıdaki `EncryptFile` yöntemi forma ekleyin.</span><span class="sxs-lookup"><span data-stu-id="325d5-179">Add the following `EncryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#5)]
 [!code-vb[CryptoWalkThru#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#5)]  
  
## <a name="decrypting-a-file"></a><span data-ttu-id="325d5-180">Dosya şifresini çözme</span><span class="sxs-lookup"><span data-stu-id="325d5-180">Decrypting a File</span></span>  

<span data-ttu-id="325d5-181">Bu görev iki yöntem içerir, düğme için olay işleyicisi yöntemi `Decrypt File` ( `buttonDecryptFile_Click` ) ve `DecryptFile` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="325d5-181">This task involves two methods, the event handler method for the `Decrypt File` button (`buttonDecryptFile_Click`), and the `DecryptFile` method.</span></span> <span data-ttu-id="325d5-182">İlk yöntem bir dosya seçmek için bir iletişim kutusu görüntüler ve dosya adını şifre çözme işlemini gerçekleştiren ikinci yönteme geçirir.</span><span class="sxs-lookup"><span data-stu-id="325d5-182">The first method displays a dialog box for selecting a file and passes its file name to the second method, which performs the decryption.</span></span>  
  
<span data-ttu-id="325d5-183">`Decrypt`Yöntemi aşağıdakileri yapar:</span><span class="sxs-lookup"><span data-stu-id="325d5-183">The `Decrypt` method does the following:</span></span>  
  
1. <span data-ttu-id="325d5-184"><xref:System.Security.Cryptography.Aes>İçeriğin şifresini çözmek için simetrik bir algoritma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="325d5-184">Creates an <xref:System.Security.Cryptography.Aes> symmetric algorithm to decrypt the content.</span></span>  
  
2. <span data-ttu-id="325d5-185">Şifrelenmiş <xref:System.IO.FileStream> anahtarın ve IV 'nin uzunluklarının elde etmek için, şifrelenen paketin ilk sekiz baytını bayt dizilerine okur.</span><span class="sxs-lookup"><span data-stu-id="325d5-185">Reads the first eight bytes of the <xref:System.IO.FileStream> of the encrypted package into byte arrays to obtain the lengths of the encrypted key and the IV.</span></span>  
  
3. <span data-ttu-id="325d5-186">Anahtar ve IV 'yi şifreleme paketinden bayt dizilerine ayıklar.</span><span class="sxs-lookup"><span data-stu-id="325d5-186">Extracts the key and IV from the encryption package into byte arrays.</span></span>  
  
4. <span data-ttu-id="325d5-187"><xref:System.Security.Cryptography.RSACryptoServiceProvider>Anahtarın şifresini çözmek için bir nesne oluşturur <xref:System.Security.Cryptography.Aes> .</span><span class="sxs-lookup"><span data-stu-id="325d5-187">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to decrypt the <xref:System.Security.Cryptography.Aes> key.</span></span>  
  
5. <span data-ttu-id="325d5-188"><xref:System.Security.Cryptography.CryptoStream> <xref:System.IO.FileStream> Şifreleme paketinin, bayt blokları içindeki şifre metin bölümünü, <xref:System.IO.FileStream> şifresi çözülmüş dosya için nesnesine okumak ve şifresini çözmek için bir nesnesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="325d5-188">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and decrypt the cipher text section of the <xref:System.IO.FileStream> encryption package, in blocks of bytes, into the <xref:System.IO.FileStream> object for the decrypted file.</span></span> <span data-ttu-id="325d5-189">Bu tamamlandığında şifre çözme işlemi tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="325d5-189">When this is finished, the decryption is completed.</span></span>  
  
 <span data-ttu-id="325d5-190">`Click`Düğme için olay işleyicisi olarak aşağıdaki kodu ekleyin `Decrypt File` .</span><span class="sxs-lookup"><span data-stu-id="325d5-190">Add the following code as the `Click` event handler for the `Decrypt File` button.</span></span>  
  
 [!code-csharp[CryptoWalkThru#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#4)]
 [!code-vb[CryptoWalkThru#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#4)]  
  
 <span data-ttu-id="325d5-191">Aşağıdaki `DecryptFile` yöntemi forma ekleyin.</span><span class="sxs-lookup"><span data-stu-id="325d5-191">Add the following `DecryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#6)]
 [!code-vb[CryptoWalkThru#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#6)]  
  
## <a name="exporting-a-public-key"></a><span data-ttu-id="325d5-192">Ortak anahtar dışarı aktarılıyor</span><span class="sxs-lookup"><span data-stu-id="325d5-192">Exporting a Public Key</span></span>

<span data-ttu-id="325d5-193">Bu görev düğme tarafından oluşturulan anahtarı `Create Keys` bir dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="325d5-193">This task saves the key created by the `Create Keys` button to a file.</span></span> <span data-ttu-id="325d5-194">Yalnızca ortak parametreleri dışarı aktarır.</span><span class="sxs-lookup"><span data-stu-id="325d5-194">It exports only the public parameters.</span></span>  
  
<span data-ttu-id="325d5-195">Bu görev, Gamze 'nin kendi ortak anahtarını veren senaryosuna benzetir. böylece, dosyaları şifreleyebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="325d5-195">This task simulates the scenario of Alice giving Bob her public key so that he can encrypt files for her.</span></span> <span data-ttu-id="325d5-196">Ortak anahtara sahip olan kişiler ve özel parametrelerle tam anahtar çiftine sahip olmadıkları için şifrelerini çözemeyecektir.</span><span class="sxs-lookup"><span data-stu-id="325d5-196">He and others who have that public key will not be able to decrypt them because they do not have the full key pair with private parameters.</span></span>  
  
<span data-ttu-id="325d5-197">`Click`Düğme () için olay işleyicisi olarak aşağıdaki kodu ekleyin `Export Public Key` `buttonExportPublicKey_Click` .</span><span class="sxs-lookup"><span data-stu-id="325d5-197">Add the following code as the `Click` event handler for the `Export Public Key` button (`buttonExportPublicKey_Click`).</span></span>  
  
[!code-csharp[CryptoWalkThru#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#8)]
[!code-vb[CryptoWalkThru#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#8)]  
  
## <a name="importing-a-public-key"></a><span data-ttu-id="325d5-198">Ortak anahtar içeri aktarılıyor</span><span class="sxs-lookup"><span data-stu-id="325d5-198">Importing a Public Key</span></span>

<span data-ttu-id="325d5-199">Bu görev, anahtarı, düğme tarafından oluşturulan yalnızca ortak parametrelerle yükler `Export Public Key` ve anahtar kapsayıcısı adı olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="325d5-199">This task loads the key with only public parameters, as created by the `Export Public Key` button, and sets it as the key container name.</span></span>  
  
<span data-ttu-id="325d5-200">Bu görev, can 'ın, dosyalarını şifreleyebilmesi için Çiğdem 'in anahtarını yalnızca ortak parametrelerle yükleyen emre 'nin senaryosuna benzetir.</span><span class="sxs-lookup"><span data-stu-id="325d5-200">This task simulates the scenario of Bob loading Alice's key with only public parameters so he can encrypt files for her.</span></span>  
  
<span data-ttu-id="325d5-201">`Click`Düğme () için olay işleyicisi olarak aşağıdaki kodu ekleyin `Import Public Key` `buttonImportPublicKey_Click` .</span><span class="sxs-lookup"><span data-stu-id="325d5-201">Add the following code as the `Click` event handler for the `Import Public Key` button (`buttonImportPublicKey_Click`).</span></span>  
  
[!code-csharp[CryptoWalkThru#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#9)]
[!code-vb[CryptoWalkThru#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#9)]  
  
## <a name="getting-a-private-key"></a><span data-ttu-id="325d5-202">Özel anahtar alma</span><span class="sxs-lookup"><span data-stu-id="325d5-202">Getting a Private Key</span></span>  

<span data-ttu-id="325d5-203">Bu görev, anahtar kapsayıcısı adını düğme kullanılarak oluşturulan anahtarın adına ayarlar `Create Keys` .</span><span class="sxs-lookup"><span data-stu-id="325d5-203">This task sets the key container name to the name of the key created by using the `Create Keys` button.</span></span> <span data-ttu-id="325d5-204">Anahtar kapsayıcısı, özel parametrelerle tam anahtar çiftini içerir.</span><span class="sxs-lookup"><span data-stu-id="325d5-204">The key container will contain the full key pair with private parameters.</span></span>  
  
<span data-ttu-id="325d5-205">Bu görev, Bob tarafından şifrelenen dosyaların şifresini çözmek için özel anahtarını kullanarak Gamze 'nin senaryosuna benzetir.</span><span class="sxs-lookup"><span data-stu-id="325d5-205">This task simulates the scenario of Alice using her private key to decrypt files encrypted by Bob.</span></span>  
  
<span data-ttu-id="325d5-206">`Click`Düğme () için olay işleyicisi olarak aşağıdaki kodu ekleyin `Get Private Key` `buttonGetPrivateKey_Click` .</span><span class="sxs-lookup"><span data-stu-id="325d5-206">Add the following code as the `Click` event handler for the `Get Private Key` button (`buttonGetPrivateKey_Click`).</span></span>  
  
[!code-csharp[CryptoWalkThru#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#7)]
[!code-vb[CryptoWalkThru#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#7)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="325d5-207">Uygulamayı Test Etme</span><span class="sxs-lookup"><span data-stu-id="325d5-207">Testing the Application</span></span>

<span data-ttu-id="325d5-208">Uygulamayı oluşturduktan sonra, aşağıdaki test senaryolarını gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="325d5-208">After you have built the application, perform the following testing scenarios.</span></span>  
  
#### <a name="to-create-keys-encrypt-and-decrypt"></a><span data-ttu-id="325d5-209">Anahtar oluşturmak, şifrelemek ve şifresini çözmek için</span><span class="sxs-lookup"><span data-stu-id="325d5-209">To create keys, encrypt, and decrypt</span></span>  
  
1. <span data-ttu-id="325d5-210">`Create Keys` düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="325d5-210">Click the `Create Keys` button.</span></span> <span data-ttu-id="325d5-211">Etiket, anahtar adını gösterir ve tam bir anahtar çifti olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="325d5-211">The label displays the key name and shows that it is a full key pair.</span></span>  
  
2. <span data-ttu-id="325d5-212">`Export Public Key` düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="325d5-212">Click the `Export Public Key` button.</span></span> <span data-ttu-id="325d5-213">Ortak anahtar parametrelerini dışa aktarmanın geçerli anahtarı değiştirmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="325d5-213">Note that exporting the public key parameters does not change the current key.</span></span>  
  
3. <span data-ttu-id="325d5-214">Düğmesine tıklayın `Encrypt File` ve bir dosya seçin.</span><span class="sxs-lookup"><span data-stu-id="325d5-214">Click the `Encrypt File` button and select a file.</span></span>  
  
4. <span data-ttu-id="325d5-215">Düğmesine tıklayın `Decrypt File` ve yeni şifrelenen dosyayı seçin.</span><span class="sxs-lookup"><span data-stu-id="325d5-215">Click the `Decrypt File` button and select the file just encrypted.</span></span>  
  
5. <span data-ttu-id="325d5-216">Yalnızca şifresi çözülen dosyayı inceleyin.</span><span class="sxs-lookup"><span data-stu-id="325d5-216">Examine the file just decrypted.</span></span>  
  
6. <span data-ttu-id="325d5-217">Uygulamayı kapatın ve sonraki senaryoda kalıcı anahtar kapsayıcıları almayı sınamak için yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="325d5-217">Close the application and restart it to test retrieving persisted key containers in the next scenario.</span></span>  
  
#### <a name="to-encrypt-using-the-public-key"></a><span data-ttu-id="325d5-218">Ortak anahtar kullanarak şifrelemek için</span><span class="sxs-lookup"><span data-stu-id="325d5-218">To encrypt using the public key</span></span>  
  
1. <span data-ttu-id="325d5-219">`Import Public Key` düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="325d5-219">Click the `Import Public Key` button.</span></span> <span data-ttu-id="325d5-220">Etiket, anahtar adını görüntüler ve yalnızca ortak olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="325d5-220">The label displays the key name and shows that it is public only.</span></span>  
  
2. <span data-ttu-id="325d5-221">Düğmesine tıklayın `Encrypt File` ve bir dosya seçin.</span><span class="sxs-lookup"><span data-stu-id="325d5-221">Click the `Encrypt File` button and select a file.</span></span>  
  
3. <span data-ttu-id="325d5-222">Düğmesine tıklayın `Decrypt File` ve yeni şifrelenen dosyayı seçin.</span><span class="sxs-lookup"><span data-stu-id="325d5-222">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="325d5-223">Bu işlem başarısız olur çünkü şifresini çözmek için özel anahtarınız olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="325d5-223">This will fail because you must have the private key to decrypt.</span></span>  
  
 <span data-ttu-id="325d5-224">Bu senaryoda, bir dosyayı başka bir kişiye şifrelemek için yalnızca ortak anahtarın bulunması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="325d5-224">This scenario demonstrates having only the public key to encrypt a file for another person.</span></span> <span data-ttu-id="325d5-225">Genellikle bu kişi size yalnızca ortak anahtar verir ve şifre çözme için özel anahtarı karıştı.</span><span class="sxs-lookup"><span data-stu-id="325d5-225">Typically that person would give you only the public key and withhold the private key for decryption.</span></span>  
  
#### <a name="to-decrypt-using-the-private-key"></a><span data-ttu-id="325d5-226">Özel anahtarı kullanarak şifresini çözmek için</span><span class="sxs-lookup"><span data-stu-id="325d5-226">To decrypt using the private key</span></span>  
  
1. <span data-ttu-id="325d5-227">`Get Private Key` düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="325d5-227">Click the `Get Private Key` button.</span></span> <span data-ttu-id="325d5-228">Etiket, anahtar adını görüntüler ve tam anahtar çifti olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="325d5-228">The label displays the key name and shows whether it is the full key pair.</span></span>  
  
2. <span data-ttu-id="325d5-229">Düğmesine tıklayın `Decrypt File` ve yeni şifrelenen dosyayı seçin.</span><span class="sxs-lookup"><span data-stu-id="325d5-229">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="325d5-230">Şifresini çözmek için tam anahtar çiftine sahip olduğunuzdan bu işlem başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="325d5-230">This will be successful because you have the full key pair to decrypt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="325d5-231">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="325d5-231">See also</span></span>

- <span data-ttu-id="325d5-232">[Şifreleme modeli](cryptography-model.md) -şifrelemenin temel sınıf kitaplığında nasıl uygulandığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="325d5-232">[Cryptography Model](cryptography-model.md) - Describes how cryptography is implemented in the base class library.</span></span>
- [<span data-ttu-id="325d5-233">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="325d5-233">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="325d5-234">Platformlar arası şifreleme</span><span class="sxs-lookup"><span data-stu-id="325d5-234">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="325d5-235">ASP.NET Core veri koruma</span><span class="sxs-lookup"><span data-stu-id="325d5-235">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
