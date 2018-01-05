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
# <a name="walkthrough-creating-a-cryptographic-application"></a><span data-ttu-id="9f1ee-102">İzlenecek Yol: Şifreleme Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9f1ee-102">Walkthrough: Creating a Cryptographic Application</span></span>
<span data-ttu-id="9f1ee-103">Bu kılavuz, şifrelemek ve içeriğin şifresini gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-103">This walkthrough demonstrates how to encrypt and decrypt content.</span></span> <span data-ttu-id="9f1ee-104">Kod örnekleri, bir Windows Forms uygulaması için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-104">The code examples are designed for a Windows Forms application.</span></span> <span data-ttu-id="9f1ee-105">Bu uygulamayı gerçek dünya senaryoları, akıllı kart kullanma gibi gösterilmemiştir.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-105">This application does not demonstrate real world scenarios, such as using smart cards.</span></span> <span data-ttu-id="9f1ee-106">Bunun yerine, şifreleme ve şifre çözme temelleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-106">Instead, it demonstrates the fundamentals of encryption and decryption.</span></span>  
  
 <span data-ttu-id="9f1ee-107">Bu kılavuz aşağıdaki yönergeleri için şifreleme kullanır:</span><span class="sxs-lookup"><span data-stu-id="9f1ee-107">This walkthrough uses the following guidelines for encryption:</span></span>  
  
-   <span data-ttu-id="9f1ee-108">Kullanım <xref:System.Security.Cryptography.RijndaelManaged> sınıfı, şifrelemek ve kendi otomatik olarak oluşturulan kullanarak verilerin şifresini çözmek için bir simetrik algoritması <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> ve <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-108">Use the <xref:System.Security.Cryptography.RijndaelManaged> class, a symmetric algorithm, to encrypt and decrypt data by using its automatically generated <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> and <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>.</span></span>  
  
-   <span data-ttu-id="9f1ee-109">Kullanım <xref:System.Security.Cryptography.RSACryptoServiceProvider>, şifrelemek ve tarafından şifrelenmiş verilere anahtarın şifresini çözmek için bir asimetrik algoritma <xref:System.Security.Cryptography.RijndaelManaged>.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-109">Use the <xref:System.Security.Cryptography.RSACryptoServiceProvider>, an asymmetric algorithm, to encrypt and decrypt the key to the data encrypted by <xref:System.Security.Cryptography.RijndaelManaged>.</span></span> <span data-ttu-id="9f1ee-110">Asimetrik algoritmalar, en iyi daha küçük miktarda bir anahtarı gibi veriler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-110">Asymmetric algorithms are best used for smaller amounts of data, such as a key.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9f1ee-111">Diğer kişilerle şifrelenmiş içerik değişimi yerine, bilgisayarınızdaki verileri korumak istiyorsanız, kullanmayı <xref:System.Security.Cryptography.ProtectedData> veya <xref:System.Security.Cryptography.ProtectedMemory> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-111">If you want to protect data on your computer instead of exchanging encrypted content with other people, consider using the <xref:System.Security.Cryptography.ProtectedData> or <xref:System.Security.Cryptography.ProtectedMemory> classes.</span></span>  
  
 <span data-ttu-id="9f1ee-112">Bu konu başlığı altındaki şifreleme görevleri aşağıdaki tabloda özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-112">The following table summarizes the cryptographic tasks in this topic.</span></span>  
  
|<span data-ttu-id="9f1ee-113">Görev</span><span class="sxs-lookup"><span data-stu-id="9f1ee-113">Task</span></span>|<span data-ttu-id="9f1ee-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f1ee-114">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="9f1ee-115">Bir Windows Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="9f1ee-115">Creating a Windows Forms application</span></span>|<span data-ttu-id="9f1ee-116">Uygulamayı çalıştırmak için gerekli denetimleri listeler.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-116">Lists the controls that are required to run the application.</span></span>|  
|<span data-ttu-id="9f1ee-117">Genel nesne bildirme</span><span class="sxs-lookup"><span data-stu-id="9f1ee-117">Declaring global objects</span></span>|<span data-ttu-id="9f1ee-118">Yol değişkenleri, dize bildirir <xref:System.Security.Cryptography.CspParameters>ve <xref:System.Security.Cryptography.RSACryptoServiceProvider> genel bağlamında olmasını <xref:System.Windows.Forms.Form> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-118">Declares string path variables, the <xref:System.Security.Cryptography.CspParameters>, and the <xref:System.Security.Cryptography.RSACryptoServiceProvider> to have global context of the <xref:System.Windows.Forms.Form> class.</span></span>|  
|<span data-ttu-id="9f1ee-119">Asimetrik anahtar oluşturma</span><span class="sxs-lookup"><span data-stu-id="9f1ee-119">Creating an asymmetric key</span></span>|<span data-ttu-id="9f1ee-120">Asimetrik ortak ve özel anahtar değer çifti oluşturur ve bir anahtar kapsayıcı adı atar.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-120">Creates an asymmetric public and private key value pair and assigns it a key container name.</span></span>|  
|<span data-ttu-id="9f1ee-121">Bir dosya şifreleme</span><span class="sxs-lookup"><span data-stu-id="9f1ee-121">Encrypting a file</span></span>|<span data-ttu-id="9f1ee-122">Dosyayı şifreler ve şifreleme için bir dosya seçmek için bir iletişim kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-122">Displays a dialog box to select a file for encryption and encrypts the file.</span></span>|  
|<span data-ttu-id="9f1ee-123">Bir dosyanın şifresini çözmek üzere</span><span class="sxs-lookup"><span data-stu-id="9f1ee-123">Decrypting a file</span></span>|<span data-ttu-id="9f1ee-124">Dosyanın şifresini çözer ve şifre çözme için şifrelenmiş bir dosya seçmek için bir iletişim kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-124">Displays a dialog box to select an encrypted file for decryption and decrypts the file.</span></span>|  
|<span data-ttu-id="9f1ee-125">Bir özel anahtar alma</span><span class="sxs-lookup"><span data-stu-id="9f1ee-125">Getting a private key</span></span>|<span data-ttu-id="9f1ee-126">Anahtar kapsayıcı adı kullanarak tam anahtar çifti alır.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-126">Gets the full key pair using the key container name.</span></span>|  
|<span data-ttu-id="9f1ee-127">Bir ortak anahtar dışarı aktarma</span><span class="sxs-lookup"><span data-stu-id="9f1ee-127">Exporting a public key</span></span>|<span data-ttu-id="9f1ee-128">Yalnızca ortak parametreleri içeren bir XML dosyası için anahtar kaydeder.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-128">Saves the key to an XML file with only public parameters.</span></span>|  
|<span data-ttu-id="9f1ee-129">Bir ortak anahtar alma</span><span class="sxs-lookup"><span data-stu-id="9f1ee-129">Importing a public key</span></span>|<span data-ttu-id="9f1ee-130">Anahtar bir XML dosyasından anahtar kapsayıcısına yükler.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-130">Loads the key from an XML file into the key container.</span></span>|  
|<span data-ttu-id="9f1ee-131">Uygulamayı test etme</span><span class="sxs-lookup"><span data-stu-id="9f1ee-131">Testing the application</span></span>|<span data-ttu-id="9f1ee-132">Bu uygulamayı test etmek için yordamları listeler.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-132">Lists procedures for testing this application.</span></span>|  
  
## <a name="prerequisites"></a><span data-ttu-id="9f1ee-133">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="9f1ee-133">Prerequisites</span></span>  
 <span data-ttu-id="9f1ee-134">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="9f1ee-134">You need the following components to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="9f1ee-135">Başvurular <xref:System.IO> ve <xref:System.Security.Cryptography> ad alanları.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-135">References to the <xref:System.IO> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
## <a name="creating-a-windows-forms-application"></a><span data-ttu-id="9f1ee-136">Bir Windows Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="9f1ee-136">Creating a Windows Forms Application</span></span>  
 <span data-ttu-id="9f1ee-137">Bu kılavuzda kod örnekleri çoğu düğmesi denetimleri için olay işleyicileri olacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-137">Most of the code examples in this walkthrough are designed to be event handlers for button controls.</span></span> <span data-ttu-id="9f1ee-138">Aşağıdaki tabloda, kod örnekleri eşleştirmek örnek uygulama ve gerekli adları için gerekli denetimleri listeler.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-138">The following table lists the controls required for the sample application and their required names to match the code examples.</span></span>  
  
|<span data-ttu-id="9f1ee-139">Denetim</span><span class="sxs-lookup"><span data-stu-id="9f1ee-139">Control</span></span>|<span data-ttu-id="9f1ee-140">Ad</span><span class="sxs-lookup"><span data-stu-id="9f1ee-140">Name</span></span>|<span data-ttu-id="9f1ee-141">(Gerektiğinde) metin özelliği</span><span class="sxs-lookup"><span data-stu-id="9f1ee-141">Text property (as needed)</span></span>|  
|-------------|----------|---------------------------------|  
|<xref:System.Windows.Forms.Button>|`buttonEncryptFile`|<span data-ttu-id="9f1ee-142">Dosya şifreleme</span><span class="sxs-lookup"><span data-stu-id="9f1ee-142">Encrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonDecryptFile`|<span data-ttu-id="9f1ee-143">Dosyanın şifresini çözme</span><span class="sxs-lookup"><span data-stu-id="9f1ee-143">Decrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonCreateAsmKeys`|<span data-ttu-id="9f1ee-144">Anahtarları oluştur</span><span class="sxs-lookup"><span data-stu-id="9f1ee-144">Create Keys</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonExportPublicKey`|<span data-ttu-id="9f1ee-145">Ortak anahtar dışarı aktarma</span><span class="sxs-lookup"><span data-stu-id="9f1ee-145">Export Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonImportPublicKey`|<span data-ttu-id="9f1ee-146">İçeri aktarma ortak anahtar</span><span class="sxs-lookup"><span data-stu-id="9f1ee-146">Import Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonGetPrivateKey`|<span data-ttu-id="9f1ee-147">Özel anahtarı alma</span><span class="sxs-lookup"><span data-stu-id="9f1ee-147">Get Private Key</span></span>|  
|<xref:System.Windows.Forms.Label>|`label1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog2`||  
  
 <span data-ttu-id="9f1ee-148">Kendi olay işleyicileri oluşturmak için Visual Studio Tasarımcısı'nda düğmeleri çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-148">Double-click the buttons in the  Visual Studio designer to create their event handlers.</span></span>  
  
## <a name="declaring-global-objects"></a><span data-ttu-id="9f1ee-149">Genel nesne bildirme</span><span class="sxs-lookup"><span data-stu-id="9f1ee-149">Declaring Global Objects</span></span>  
 <span data-ttu-id="9f1ee-150">Aşağıdaki kod formun oluşturucuyu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-150">Add the following code to the Form's constructor.</span></span> <span data-ttu-id="9f1ee-151">Ortamınız ve tercihlerinizle dize değişkenleri düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-151">Edit the string variables for your environment and preferences.</span></span>  
  
 [!code-csharp[CryptoWalkThru#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#1)]
 [!code-vb[CryptoWalkThru#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#1)]  
  
## <a name="creating-an-asymmetric-key"></a><span data-ttu-id="9f1ee-152">Asimetrik anahtar oluşturma</span><span class="sxs-lookup"><span data-stu-id="9f1ee-152">Creating an Asymmetric Key</span></span>  
 <span data-ttu-id="9f1ee-153">Bu görev şifreler ve şifresini çözer bir asimetrik anahtar oluşturur <xref:System.Security.Cryptography.RijndaelManaged> anahtarı.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-153">This task creates an asymmetric key that encrypts and decrypts the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span> <span data-ttu-id="9f1ee-154">Bu anahtar, içeriği şifrelemek için kullanılan ve etiket denetimi anahtar kapsayıcı adı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-154">This key was used to encrypt the content and it displays the key container name on the label control.</span></span>  
  
 <span data-ttu-id="9f1ee-155">Aşağıdaki kodu olarak ekleme `Click` için olay işleyicisini `Create Keys` düğmesi (`buttonCreateAsmKeys_Click`).</span><span class="sxs-lookup"><span data-stu-id="9f1ee-155">Add the following code as the `Click` event handler for the `Create Keys` button (`buttonCreateAsmKeys_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#2)]
 [!code-vb[CryptoWalkThru#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#2)]  
  
## <a name="encrypting-a-file"></a><span data-ttu-id="9f1ee-156">Bir dosya şifreleme</span><span class="sxs-lookup"><span data-stu-id="9f1ee-156">Encrypting a File</span></span>  
 <span data-ttu-id="9f1ee-157">Bu görev, iki yöntem içerir: olay işleyicisi yöntemi için `Encrypt File` düğmesi (`buttonEncryptFile_Click`) ve `EncryptFile` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-157">This task involves two methods: the event handler method for the `Encrypt File` button (`buttonEncryptFile_Click`) and the `EncryptFile` method.</span></span> <span data-ttu-id="9f1ee-158">İlk yöntem bir dosya seçmek için bir iletişim kutusu görüntüler ve dosya adını şifreleme gerçekleştirir ikinci yöntemine geçirir.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-158">The first method displays a dialog box for selecting a file and passes the file name to the second method, which performs the encryption.</span></span>  
  
 <span data-ttu-id="9f1ee-159">Şifrelenmiş içerik, anahtar ve IV tüm birine kaydedilir <xref:System.IO.FileStream>, adlandırılır şifreleme paketi olarak.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-159">The encrypted content, key, and IV are all saved to one <xref:System.IO.FileStream>, which is referred to as the encryption package.</span></span>  
  
 <span data-ttu-id="9f1ee-160">`EncryptFile` Yöntemi aşağıdakileri yapar:</span><span class="sxs-lookup"><span data-stu-id="9f1ee-160">The `EncryptFile` method does the following:</span></span>  
  
1.  <span data-ttu-id="9f1ee-161">Oluşturur bir <xref:System.Security.Cryptography.RijndaelManaged> içeriği şifrelemek için simetrik algoritması.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-161">Creates a <xref:System.Security.Cryptography.RijndaelManaged> symmetric algorithm to encrypt the content.</span></span>  
  
2.  <span data-ttu-id="9f1ee-162">Oluşturur bir <xref:System.Security.Cryptography.RSACryptoServiceProvider> şifrelemek için nesne <xref:System.Security.Cryptography.RijndaelManaged> anahtarı.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-162">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to encrypt the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span>  
  
3.  <span data-ttu-id="9f1ee-163">Kullanan bir <xref:System.Security.Cryptography.CryptoStream> okuyun ve şifrelemek için nesne <xref:System.IO.FileStream> kaynak dosyasının baytlara bir hedef bloklarını <xref:System.IO.FileStream> şifrelenmiş dosya nesnesi.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-163">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and encrypt the <xref:System.IO.FileStream> of the source file, in blocks of bytes, into a destination <xref:System.IO.FileStream> object for the encrypted file.</span></span>  
  
4.  <span data-ttu-id="9f1ee-164">Bayt dizileri uzunluğu değerlerine oluşturur ve IV ve şifrelenmiş anahtar uzunlukları belirler.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-164">Determines the lengths of the encrypted key and IV, and creates byte arrays of their length values.</span></span>  
  
5.  <span data-ttu-id="9f1ee-165">Bu anahtar, IV ve uzunluğu değerlerine şifrelenmiş paketi yazar.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-165">Writes the Key, IV, and their length values to the encrypted package.</span></span>  
  
 <span data-ttu-id="9f1ee-166">Şifreleme paketi aşağıdaki biçimi kullanır:</span><span class="sxs-lookup"><span data-stu-id="9f1ee-166">The encryption package uses the following format:</span></span>  
  
-   <span data-ttu-id="9f1ee-167">Anahtar uzunluğu, bayt 0 - 3</span><span class="sxs-lookup"><span data-stu-id="9f1ee-167">Key length, bytes 0 - 3</span></span>  
  
-   <span data-ttu-id="9f1ee-168">IV uzunluğu, bayt 4-7</span><span class="sxs-lookup"><span data-stu-id="9f1ee-168">IV length, bytes 4 - 7</span></span>  
  
-   <span data-ttu-id="9f1ee-169">Şifrelenmiş anahtar</span><span class="sxs-lookup"><span data-stu-id="9f1ee-169">Encrypted key</span></span>  
  
-   <span data-ttu-id="9f1ee-170">IV</span><span class="sxs-lookup"><span data-stu-id="9f1ee-170">IV</span></span>  
  
-   <span data-ttu-id="9f1ee-171">Şifreli metin</span><span class="sxs-lookup"><span data-stu-id="9f1ee-171">Cipher text</span></span>  
  
 <span data-ttu-id="9f1ee-172">Başlangıç noktaları ve ardından dosyasının şifresini çözmek için kullanılan şifreleme paketinin tüm bölümlerinin uzunlukları belirlemek için IV ve anahtar uzunluklarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-172">You can use the lengths of the key and IV to determine the starting points and lengths of all parts of the encryption package, which can then be used to decrypt the file.</span></span>  
  
 <span data-ttu-id="9f1ee-173">Aşağıdaki kodu olarak ekleme `Click` için olay işleyicisini `Encrypt File` düğmesi (`buttonEncryptFile_Click`).</span><span class="sxs-lookup"><span data-stu-id="9f1ee-173">Add the following code as the `Click` event handler for the `Encrypt File` button (`buttonEncryptFile_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#3)]
 [!code-vb[CryptoWalkThru#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#3)]  
  
 <span data-ttu-id="9f1ee-174">Aşağıdakileri ekleyin `EncryptFile` forma yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-174">Add the following `EncryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#5)]
 [!code-vb[CryptoWalkThru#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#5)]  
  
## <a name="decrypting-a-file"></a><span data-ttu-id="9f1ee-175">Bir dosyanın şifresini çözmek üzere</span><span class="sxs-lookup"><span data-stu-id="9f1ee-175">Decrypting a File</span></span>  
 <span data-ttu-id="9f1ee-176">Bu görev, iki yöntem, olay işleyicisi yöntemini içerir `Decrypt File` düğmesi (`buttonEncryptFile_Click`) ve `DecryptFile` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-176">This task involves two methods, the event handler method for the `Decrypt File` button (`buttonEncryptFile_Click`), and the `DecryptFile` method.</span></span> <span data-ttu-id="9f1ee-177">İlk yöntem, bir dosya seçmek için bir iletişim kutusu görüntüler ve şifre çözme gerçekleştiren bir ikinci yöntem dosya adıyla geçirir.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-177">The first method displays a dialog box for selecting a file and passes its file name to the second method, which performs the decryption.</span></span>  
  
 <span data-ttu-id="9f1ee-178">`Decrypt` Yöntemi aşağıdakileri yapar:</span><span class="sxs-lookup"><span data-stu-id="9f1ee-178">The `Decrypt` method does the following:</span></span>  
  
1.  <span data-ttu-id="9f1ee-179">Oluşturur bir <xref:System.Security.Cryptography.RijndaelManaged> içeriğin şifresini çözmek için simetrik algoritması.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-179">Creates a <xref:System.Security.Cryptography.RijndaelManaged> symmetric algorithm to decrypt the content.</span></span>  
  
2.  <span data-ttu-id="9f1ee-180">İlk sekiz baytı okur <xref:System.IO.FileStream> şifrelenmiş anahtar ve IV uzunluklarının edinme bayt dizileri halinde şifrelenmiş paketi.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-180">Reads the first eight bytes of the <xref:System.IO.FileStream> of the encrypted package into byte arrays to obtain the lengths of the encrypted key and the IV.</span></span>  
  
3.  <span data-ttu-id="9f1ee-181">Anahtar ve IV şifreleme paketinden bayt diziye ayıklar.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-181">Extracts the key and IV from the encryption package into byte arrays.</span></span>  
  
4.  <span data-ttu-id="9f1ee-182">Oluşturur bir <xref:System.Security.Cryptography.RSACryptoServiceProvider> şifresini çözmek için nesne <xref:System.Security.Cryptography.RijndaelManaged> anahtarı.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-182">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to decrypt the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span>  
  
5.  <span data-ttu-id="9f1ee-183">Kullanan bir <xref:System.Security.Cryptography.CryptoStream> okuyun ve şifre metin bölümünü şifresini çözmek için nesne <xref:System.IO.FileStream> şifreleme paketini, bayt bloklarında içine <xref:System.IO.FileStream> şifresi çözülen dosya nesnesi.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-183">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and decrypt the cipher text section of the <xref:System.IO.FileStream> encryption package, in blocks of bytes, into the <xref:System.IO.FileStream> object for the decrypted file.</span></span> <span data-ttu-id="9f1ee-184">Bu tamamlandığında, şifre çözme tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-184">When this is finished, the decryption is completed.</span></span>  
  
 <span data-ttu-id="9f1ee-185">Aşağıdaki kodu olarak ekleme `Click` için olay işleyicisini `Decrypt File` düğmesi.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-185">Add the following code as the `Click` event handler for the `Decrypt File` button.</span></span>  
  
 [!code-csharp[CryptoWalkThru#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#4)]
 [!code-vb[CryptoWalkThru#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#4)]  
  
 <span data-ttu-id="9f1ee-186">Aşağıdakileri ekleyin `DecryptFile` forma yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-186">Add the following `DecryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#6)]
 [!code-vb[CryptoWalkThru#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#6)]  
  
## <a name="exporting-a-public-key"></a><span data-ttu-id="9f1ee-187">Bir ortak anahtar dışarı aktarma</span><span class="sxs-lookup"><span data-stu-id="9f1ee-187">Exporting a Public Key</span></span>  
 <span data-ttu-id="9f1ee-188">Bu görevi tarafından oluşturulan anahtarı kaydeder `Create Keys` bir dosyaya düğmesi.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-188">This task saves the key created by the `Create Keys` button to a file.</span></span> <span data-ttu-id="9f1ee-189">Yalnızca ortak parametreleri aktarır.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-189">It exports only the public parameters.</span></span>  
  
 <span data-ttu-id="9f1ee-190">Bu görev, böylece kendisinin dosyaları her için şifreleyebilirsiniz Bob kendi ortak anahtar vermiş Alice senaryo benzetimini yapar.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-190">This task simulates the scenario of Alice giving Bob her public key so that he can encrypt files for her.</span></span> <span data-ttu-id="9f1ee-191">Kendisinin ve başkalarının ortak anahtara sahip tam anahtar çiftinin özel parametrelere sahip olmadığı için bunların şifrelerini çözmek mümkün olmaz.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-191">He and others who have that public key will not be able to decrypt them because they do not have the full key pair with private parameters.</span></span>  
  
 <span data-ttu-id="9f1ee-192">Aşağıdaki kodu olarak ekleme `Click` için olay işleyicisini `Export Public Key` düğmesi (`buttonExportPublicKey_Click`).</span><span class="sxs-lookup"><span data-stu-id="9f1ee-192">Add the following code as the `Click` event handler for the `Export Public Key` button (`buttonExportPublicKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#8)]
 [!code-vb[CryptoWalkThru#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#8)]  
  
## <a name="importing-a-public-key"></a><span data-ttu-id="9f1ee-193">Bir ortak anahtar alma</span><span class="sxs-lookup"><span data-stu-id="9f1ee-193">Importing a Public Key</span></span>  
 <span data-ttu-id="9f1ee-194">Bu görevi yalnızca ortak parametreleriyle anahtar tarafından oluşturulan gibi yükler `Export Public Key` düğmesine tıklayın ve anahtar kapsayıcı adı olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-194">This task loads the key with only public parameters, as created by the `Export Public Key` button, and sets it as the key container name.</span></span>  
  
 <span data-ttu-id="9f1ee-195">Bu görev, kendisinin dosyaları her için şifreleyebilirsiniz şekilde yalnızca ortak parametreleri Alice'in anahtarla yüklenirken Bob senaryo benzetimini yapar.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-195">This task simulates the scenario of Bob loading Alice's key with only public parameters so he can encrypt files for her.</span></span>  
  
 <span data-ttu-id="9f1ee-196">Aşağıdaki kodu olarak ekleme `Click` için olay işleyicisini `Import Public Key` düğmesi (`buttonImportPublicKey_Click`).</span><span class="sxs-lookup"><span data-stu-id="9f1ee-196">Add the following code as the `Click` event handler for the `Import Public Key` button (`buttonImportPublicKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#9)]
 [!code-vb[CryptoWalkThru#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#9)]  
  
## <a name="getting-a-private-key"></a><span data-ttu-id="9f1ee-197">Bir özel anahtar alma</span><span class="sxs-lookup"><span data-stu-id="9f1ee-197">Getting a Private Key</span></span>  
 <span data-ttu-id="9f1ee-198">Bu görev, anahtar kapsayıcı adı kullanılarak oluşturulan anahtarın adını ayarlar `Create Keys` düğmesi.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-198">This task sets the key container name to the name of the key created by using the `Create Keys` button.</span></span> <span data-ttu-id="9f1ee-199">Anahtar kapsayıcısı özel parametrelerle tam anahtar çifti içerir.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-199">The key container will contain the full key pair with private parameters.</span></span>  
  
 <span data-ttu-id="9f1ee-200">Bu görev Bob tarafından şifrelenmiş dosyaların şifresini çözmek için kendi özel anahtarı kullanarak Alice senaryo benzetimini yapar.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-200">This task simulates the scenario of Alice using her private key to decrypt files encrypted by Bob.</span></span>  
  
 <span data-ttu-id="9f1ee-201">Aşağıdaki kodu olarak ekleme `Click` için olay işleyicisini `Get Private Key` düğmesi (`buttonGetPrivateKey_Click`).</span><span class="sxs-lookup"><span data-stu-id="9f1ee-201">Add the following code as the `Click` event handler for the `Get Private Key` button (`buttonGetPrivateKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#7)]
 [!code-vb[CryptoWalkThru#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#7)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="9f1ee-202">Uygulamayı Test Etme</span><span class="sxs-lookup"><span data-stu-id="9f1ee-202">Testing the Application</span></span>  
 <span data-ttu-id="9f1ee-203">Uygulamayı oluşturduktan sonra aşağıdaki test senaryolarını gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-203">After you have built the application, perform the following testing scenarios.</span></span>  
  
#### <a name="to-create-keys-encrypt-and-decrypt"></a><span data-ttu-id="9f1ee-204">Anahtarlar oluşturmak, şifrelemek ve şifresini çözmek için</span><span class="sxs-lookup"><span data-stu-id="9f1ee-204">To create keys, encrypt, and decrypt</span></span>  
  
1.  <span data-ttu-id="9f1ee-205">Tıklatın `Create Keys` düğmesi.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-205">Click the `Create Keys` button.</span></span> <span data-ttu-id="9f1ee-206">Etiket anahtarı adını görüntüler ve tam anahtar çifti olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-206">The label displays the key name and shows that it is a full key pair.</span></span>  
  
2.  <span data-ttu-id="9f1ee-207">Tıklatın `Export Public Key` düğmesi.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-207">Click the `Export Public Key` button.</span></span> <span data-ttu-id="9f1ee-208">Ortak anahtar parametreleri dışarı aktarma geçerli anahtar değiştirmez unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-208">Note that exporting the public key parameters does not change the current key.</span></span>  
  
3.  <span data-ttu-id="9f1ee-209">Tıklatın `Encrypt File` düğmesine tıklayın ve bir dosya seçin.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-209">Click the `Encrypt File` button and select a file.</span></span>  
  
4.  <span data-ttu-id="9f1ee-210">Tıklatın `Decrypt File` düğmesini tıklatın ve yalnızca şifrelenmiş dosya seçin.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-210">Click the `Decrypt File` button and select the file just encrypted.</span></span>  
  
5.  <span data-ttu-id="9f1ee-211">Yalnızca şifresi dosyasını inceleyin.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-211">Examine the file just decrypted.</span></span>  
  
6.  <span data-ttu-id="9f1ee-212">Uygulamayı kapatın ve İleri senaryosunda test alınırken kalıcı anahtar kapsayıcıları için yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-212">Close the application and restart it to test retrieving persisted key containers in the next scenario.</span></span>  
  
#### <a name="to-encrypt-using-the-public-key"></a><span data-ttu-id="9f1ee-213">Ortak anahtar kullanarak şifrelemek için</span><span class="sxs-lookup"><span data-stu-id="9f1ee-213">To encrypt using the public key</span></span>  
  
1.  <span data-ttu-id="9f1ee-214">Tıklatın `Import Public Key` düğmesi.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-214">Click the `Import Public Key` button.</span></span> <span data-ttu-id="9f1ee-215">Etiket anahtar adını görüntüler ve bunun yalnızca ortak olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-215">The label displays the key name and shows that it is public only.</span></span>  
  
2.  <span data-ttu-id="9f1ee-216">Tıklatın `Encrypt File` düğmesine tıklayın ve bir dosya seçin.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-216">Click the `Encrypt File` button and select a file.</span></span>  
  
3.  <span data-ttu-id="9f1ee-217">Tıklatın `Decrypt File` düğmesini tıklatın ve yalnızca şifrelenmiş dosya seçin.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-217">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="9f1ee-218">Özel anahtarın şifresini olması gerektiği için bu başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-218">This will fail because you must have the private key to decrypt.</span></span>  
  
 <span data-ttu-id="9f1ee-219">Bu senaryo için başka bir kişi bir dosyayı şifrelemek için yalnızca ortak anahtarın gösterir.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-219">This scenario demonstrates having only the public key to encrypt a file for another person.</span></span> <span data-ttu-id="9f1ee-220">Genellikle bu kişi yalnızca ortak anahtar verin ve bu şifre çözme için özel anahtar stopajdan.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-220">Typically that person would give you only the public key and withhold the private key for decryption.</span></span>  
  
#### <a name="to-decrypt-using-the-private-key"></a><span data-ttu-id="9f1ee-221">Özel anahtarı kullanarak şifresini çözmek için</span><span class="sxs-lookup"><span data-stu-id="9f1ee-221">To decrypt using the private key</span></span>  
  
1.  <span data-ttu-id="9f1ee-222">Tıklatın `Get Private Key` düğmesi.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-222">Click the `Get Private Key` button.</span></span> <span data-ttu-id="9f1ee-223">Etiket anahtarı adını görüntüler ve tam anahtar çifti olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-223">The label displays the key name and shows whether it is the full key pair.</span></span>  
  
2.  <span data-ttu-id="9f1ee-224">Tıklatın `Decrypt File` düğmesini tıklatın ve yalnızca şifrelenmiş dosya seçin.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-224">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="9f1ee-225">Şifresini çözmek için tam anahtar çifti olduğundan bu başarılı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-225">This will be successful because you have the full key pair to decrypt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f1ee-226">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9f1ee-226">See Also</span></span>  
 [<span data-ttu-id="9f1ee-227">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="9f1ee-227">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
