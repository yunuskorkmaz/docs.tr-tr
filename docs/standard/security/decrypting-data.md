---
title: "Verilerin Şifresini Çözme"
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
- data [.NET Framework], decryption
- symmetric decryption
- asymmetric decryption
- decryption
ms.assetid: 9b266b6c-a9b2-4d20-afd8-b3a0d8fd48a0
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ce442c679425e5d069a0e5e163cbe2ad46702480
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="decrypting-data"></a><span data-ttu-id="9fe2d-102">Verilerin Şifresini Çözme</span><span class="sxs-lookup"><span data-stu-id="9fe2d-102">Decrypting Data</span></span>
<span data-ttu-id="9fe2d-103">Şifre çözme şifreleme ters işlemdir.</span><span class="sxs-lookup"><span data-stu-id="9fe2d-103">Decryption is the reverse operation of encryption.</span></span> <span data-ttu-id="9fe2d-104">Gizli anahtar şifreleme için anahtar ve verileri şifrelemek için kullanılan IV bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9fe2d-104">For secret-key encryption, you must know both the key and IV that were used to encrypt the data.</span></span> <span data-ttu-id="9fe2d-105">Ortak anahtar şifrelemesi için ortak anahtarı (verileri özel anahtar kullanılarak şifrelenmiş varsa) veya özel anahtar (verileri ortak anahtar kullanılarak şifrelenmiş varsa) bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9fe2d-105">For public-key encryption, you must know either the public key (if the data was encrypted using the private key) or the private key (if the data was encrypted using the public key).</span></span>  
  
## <a name="symmetric-decryption"></a><span data-ttu-id="9fe2d-106">Simetrik şifre çözme</span><span class="sxs-lookup"><span data-stu-id="9fe2d-106">Symmetric Decryption</span></span>  
 <span data-ttu-id="9fe2d-107">Simetrik algoritmaları ile şifrelenmiş verilerin şifresinin simetrik algoritmaları ile verileri şifrelemek için kullanılan işlem aynıdır.</span><span class="sxs-lookup"><span data-stu-id="9fe2d-107">The decryption of data encrypted with symmetric algorithms is similar to the process used to encrypt data with symmetric algorithms.</span></span> <span data-ttu-id="9fe2d-108"><xref:System.Security.Cryptography.CryptoStream> Sınıfı simetrik şifreleme sınıflarıyla .NET Framework tarafından sağlanan herhangi bir yönetilen akış nesneden okunan verilerin şifresini çözmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9fe2d-108">The <xref:System.Security.Cryptography.CryptoStream> class is used with symmetric cryptography classes provided by the .NET Framework to decrypt data read from any managed stream object.</span></span>  
  
 <span data-ttu-id="9fe2d-109">Aşağıdaki örnek yeni bir örneğini oluşturmak nasıl gösterilmektedir <xref:System.Security.Cryptography.RijndaelManaged> sınıfı ve şifre çözme gerçekleştirileceği kullanan bir <xref:System.Security.Cryptography.CryptoStream> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="9fe2d-109">The following example illustrates how to create a new instance of the <xref:System.Security.Cryptography.RijndaelManaged> class and use it to perform decryption on a <xref:System.Security.Cryptography.CryptoStream> object.</span></span> <span data-ttu-id="9fe2d-110">Bu örnek önce yeni bir örneğini oluşturur **RijndaelManaged** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9fe2d-110">This example first creates a new instance of the **RijndaelManaged** class.</span></span> <span data-ttu-id="9fe2d-111">Sonraki oluşturduğu bir **CryptoStream** nesne ve yönetilen bir akış değerine adlı başlatır `MyStream`.</span><span class="sxs-lookup"><span data-stu-id="9fe2d-111">Next it creates a **CryptoStream** object and initializes it to the value of a managed stream called `MyStream`.</span></span> <span data-ttu-id="9fe2d-112">Ardından, **CreateDecryptor** yönteminden **RijndaelManaged** sınıfı, aynı anahtar ve şifreleme için kullanılan ve ardından geçirilen IV geçirilir **CryptoStream** Oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="9fe2d-112">Next, the **CreateDecryptor** method from the **RijndaelManaged** class is passed the same key and IV that was used for encryption and is then passed to the **CryptoStream** constructor.</span></span> <span data-ttu-id="9fe2d-113">Son olarak, **CryptoStreamMode.Read** numaralandırma iletilir **CryptoStream** Oluşturucusu akış okuma erişimi belirtin.</span><span class="sxs-lookup"><span data-stu-id="9fe2d-113">Finally, the **CryptoStreamMode.Read** enumeration is passed to the **CryptoStream** constructor to specify read access to the stream.</span></span>  
  
```vb  
Dim RMCrypto As New RijndaelManaged()  
Dim CryptStream As New CryptoStream(MyStream, RMCrypto.CreateDecryptor(RMCrypto.Key, RMCrypto.IV), CryptoStreamMode.Read)  
```  
  
```csharp  
RijndaelManaged RMCrypto = new RijndaelManaged();  
CryptoStream CryptStream = new CryptoStream(MyStream, RMCrypto.CreateDecryptor(Key, IV), CryptoStreamMode.Read);  
```  
  
 <span data-ttu-id="9fe2d-114">Aşağıdaki örnekte bir akış oluşturma, akış şifre çözme, akışından okuma ve akışlar kapatma tüm işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9fe2d-114">The following example shows the entire process of creating a stream, decrypting the stream, reading from the stream, and closing the streams.</span></span> <span data-ttu-id="9fe2d-115">A <xref:System.Net.Sockets.TcpListener> nesne dinleme nesnesi için bir bağlantı yapıldığında, bir ağ akış başlatır oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9fe2d-115">A <xref:System.Net.Sockets.TcpListener> object is created that initializes a network stream when a connection to the listening object is made.</span></span> <span data-ttu-id="9fe2d-116">Kullanarak ağ akışı çözülür **CryptoStream** sınıfı ve **RijndaelManaged** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9fe2d-116">The network stream is then decrypted using the **CryptoStream** class and the **RijndaelManaged** class.</span></span> <span data-ttu-id="9fe2d-117">Bu örnek anahtar ve IV değerleri ya da başarıyla aktarıldı veya silinmiş önceden üzerinde anlaşmaya varılan olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="9fe2d-117">This example assumes that the key and IV values have been either successfully transferred or previously agreed upon.</span></span> <span data-ttu-id="9fe2d-118">Şifrelemek ve bu değerleri aktarmak için gereken kod göstermez.</span><span class="sxs-lookup"><span data-stu-id="9fe2d-118">It does not show the code needed to encrypt and transfer these values.</span></span>  
  
```vb  
Imports System  
Imports System.Net.Sockets  
Imports System.Threading  
Imports System.IO  
Imports System.Net  
Imports System.Security.Cryptography  
  
Module Module1  
    Sub Main()  
            'The key and IV must be the same values that were used  
            'to encrypt the stream.    
            Dim Key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
            Dim IV As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
        Try  
            'Initialize a TCPListener on port 11000  
            'using the current IP address.  
            Dim TCPListen As New TcpListener(IPAddress.Any, 11000)  
  
            'Start the listener.  
            TCPListen.Start()  
  
            'Check for a connection every five seconds.  
            While Not TCPListen.Pending()  
                Console.WriteLine("Still listening. Will try in 5 seconds.")  
  
                Thread.Sleep(5000)  
            End While  
  
            'Accept the client if one is found.  
            Dim TCP As TcpClient = TCPListen.AcceptTcpClient()  
  
            'Create a network stream from the connection.  
            Dim NetStream As NetworkStream = TCP.GetStream()  
  
            'Create a new instance of the RijndaelManaged class  
            'and decrypt the stream.  
            Dim RMCrypto As New RijndaelManaged()  
  
            'Create an instance of the CryptoStream class, pass it the NetworkStream, and decrypt   
            'it with the Rijndael class using the key and IV.  
            Dim CryptStream As New CryptoStream(NetStream, RMCrypto.CreateDecryptor(Key, IV), CryptoStreamMode.Read)  
  
            'Read the stream.  
            Dim SReader As New StreamReader(CryptStream)  
  
            'Display the message.  
            Console.WriteLine("The decrypted original message: {0}", SReader.ReadToEnd())  
  
            'Close the streams.  
            SReader.Close()  
            NetStream.Close()  
            TCP.Close()  
            'Catch any exceptions.   
        Catch  
            Console.WriteLine("The Listener Failed.")  
        End Try  
    End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Net.Sockets;  
using System.Threading;  
using System.IO;  
using System.Net;  
using System.Security.Cryptography;  
  
class Class1  
{  
   static void Main(string[] args)  
   {  
      //The key and IV must be the same values that were used  
      //to encrypt the stream.    
      byte[] Key = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
      byte[] IV = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
      try  
      {  
         //Initialize a TCPListener on port 11000  
         //using the current IP address.  
         TcpListener TCPListen = new TcpListener(IPAdress.Any, 11000);  
  
         //Start the listener.  
         TCPListen.Start();  
  
         //Check for a connection every five seconds.  
         while(!TCPListen.Pending())  
         {  
            Console.WriteLine("Still listening. Will try in 5 seconds.");  
            Thread.Sleep(5000);  
         }  
  
         //Accept the client if one is found.  
         TcpClient TCP = TCPListen.AcceptTcpClient();  
  
         //Create a network stream from the connection.  
         NetworkStream NetStream = TCP.GetStream();  
  
         //Create a new instance of the RijndaelManaged class  
         // and decrypt the stream.  
         RijndaelManaged RMCrypto = new RijndaelManaged();  
  
         //Create a CryptoStream, pass it the NetworkStream, and decrypt   
         //it with the Rijndael class using the key and IV.  
         CryptoStream CryptStream = new CryptoStream(NetStream,   
            RMCrypto.CreateDecryptor(Key, IV),   
            CryptoStreamMode.Read);  
  
         //Read the stream.  
         StreamReader SReader = new StreamReader(CryptStream);  
  
         //Display the message.  
         Console.WriteLine("The decrypted original message: {0}", SReader.ReadToEnd());  
  
         //Close the streams.  
         SReader.Close();  
         NetStream.Close();  
         TCP.Close();  
      }  
      //Catch any exceptions.   
      catch  
      {  
         Console.WriteLine("The Listener Failed.");  
      }  
   }  
}  
```  
  
 <span data-ttu-id="9fe2d-119">Önceki örnek çalışmaya şifreli bir bağlantı için dinleyici yapılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9fe2d-119">For the previous sample to work, an encrypted connection must be made to the listener.</span></span> <span data-ttu-id="9fe2d-120">Bağlantı anahtarı, IV ve dinleyicisinde kullanılan algoritmasını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9fe2d-120">The connection must use the same key, IV, and algorithm used in the listener.</span></span> <span data-ttu-id="9fe2d-121">Böyle bir bağlantı yapıldığında, iletinin şifresi ve konsolda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9fe2d-121">If such a connection is made, the message is decrypted and displayed to the console.</span></span>  
  
## <a name="asymmetric-decryption"></a><span data-ttu-id="9fe2d-122">Asimetrik şifre çözme</span><span class="sxs-lookup"><span data-stu-id="9fe2d-122">Asymmetric Decryption</span></span>  
 <span data-ttu-id="9fe2d-123">Genellikle, bir taraf (taraf A) hem bir ortak ve özel anahtarı oluşturur ve bellekte veya şifreleme anahtar kapsayıcısı anahtarı depolar.</span><span class="sxs-lookup"><span data-stu-id="9fe2d-123">Typically, a party (party A) generates both a public and private key and stores the key either in memory or in a cryptographic key container.</span></span>  <span data-ttu-id="9fe2d-124">Taraflı bir daha sonra başka bir tarafa (taraf B) ortak anahtar gönderir.</span><span class="sxs-lookup"><span data-stu-id="9fe2d-124">Party A then sends the public key to another party (party B).</span></span>  <span data-ttu-id="9fe2d-125">Ortak anahtar kullanarak, B tarafı verileri şifreler ve verileri taraf A'ya gönderir.  Verileri aldıktan sonra taraf A karşılık gelen özel anahtarı kullanarak şifresini çözer.</span><span class="sxs-lookup"><span data-stu-id="9fe2d-125">Using the public key, party B encrypts data and sends the data back to party A.  After receiving the data, party A decrypts it using the private key that corresponds.</span></span>  <span data-ttu-id="9fe2d-126">Şifre çözme yalnızca taraf bir taraf B verileri şifrelemek için kullanılan ortak anahtara karşılık gelen özel anahtarı kullanıyorsa başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="9fe2d-126">Decryption will be successful only if party A uses the private key that corresponds to the public key Party B used to encrypt the data.</span></span>  
  
 <span data-ttu-id="9fe2d-127">Güvenli şifreleme anahtar kapsayıcı ve daha sonra asimetrik anahtar almak nasıl bir asimetrik anahtar depolama hakkında bilgi için bkz: [nasıl yapılır: bir anahtar kapsayıcısında asimetrik anahtarlar depolama](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).</span><span class="sxs-lookup"><span data-stu-id="9fe2d-127">For information on how to store an asymmetric key in secure cryptographic key container and how to later retrieve the asymmetric key, see [How to: Store Asymmetric Keys in a Key Container](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>  
  
 <span data-ttu-id="9fe2d-128">Aşağıdaki örnek, bir simetrik anahtar ve IV sunan bayt dizilerinin şifrelerinin gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9fe2d-128">The following example illustrates the decryption of two arrays of bytes that represent a symmetric key and IV.</span></span>  <span data-ttu-id="9fe2d-129">Asimetrik ortak anahtarı ile ayıklamak hakkında bilgi için <xref:System.Security.Cryptography.RSACryptoServiceProvider> nesne kolayca gönderebilirsiniz bkz bir üçüncü taraf bir biçimde [veri şifreleme](../../../docs/standard/security/encrypting-data.md).</span><span class="sxs-lookup"><span data-stu-id="9fe2d-129">For information on how to extract the asymmetric public key from the <xref:System.Security.Cryptography.RSACryptoServiceProvider> object in a format that you can easily send to a third party, see [Encrypting Data](../../../docs/standard/security/encrypting-data.md).</span></span>  
  
```vb  
'Create a new instance of the RSACryptoServiceProvider class.  
Dim RSA As New RSACryptoServiceProvider()  
  
' Export the public key information and send it to a third party.  
' Wait for the third party to encrypt some data and send it back.  
  
'Decrypt the symmetric key and IV.  
SymmetricKey = RSA.Decrypt(EncryptedSymmetricKey, False)  
SymmetricIV = RSA.Decrypt(EncryptedSymmetricIV, False)  
```  
  
```csharp  
//Create a new instance of the RSACryptoServiceProvider class.  
RSACryptoServiceProvider RSA = new RSACryptoServiceProvider();  
  
// Export the public key information and send it to a third party.  
// Wait for the third party to encrypt some data and send it back.  
  
//Decrypt the symmetric key and IV.  
SymmetricKey = RSA.Decrypt( EncryptedSymmetricKey, false);  
SymmetricIV = RSA.Decrypt( EncryptedSymmetricIV , false);  
```  
  
## <a name="see-also"></a><span data-ttu-id="9fe2d-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9fe2d-130">See Also</span></span>  
 [<span data-ttu-id="9fe2d-131">Şifreleme ve Şifre Çözme için Anahtarlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9fe2d-131">Generating Keys for Encryption and Decryption</span></span>](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)  
 [<span data-ttu-id="9fe2d-132">Veri Şifreleme</span><span class="sxs-lookup"><span data-stu-id="9fe2d-132">Encrypting Data</span></span>](../../../docs/standard/security/encrypting-data.md)  
 [<span data-ttu-id="9fe2d-133">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="9fe2d-133">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
