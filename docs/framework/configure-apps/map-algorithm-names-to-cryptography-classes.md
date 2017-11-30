---
title: "Algoritma Adlarını Şifreleme Sınıflarıyla Eşleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e59b2551545b8b70bcb54a5d43d041c44579b786
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a><span data-ttu-id="ffade-102">Algoritma Adlarını Şifreleme Sınıflarıyla Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="ffade-102">Mapping Algorithm Names to Cryptography Classes</span></span>
<span data-ttu-id="ffade-103">Bir geliştirici, şifreleme nesnesini kullanarak oluşturabilirsiniz dört yolla [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="ffade-103">There are four ways a developer can create a cryptography object using the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]:</span></span>  
  
-   <span data-ttu-id="ffade-104">Kullanarak bir nesne oluşturma **yeni** işleci.</span><span class="sxs-lookup"><span data-stu-id="ffade-104">Create an object by using the **new** operator.</span></span>  
  
-   <span data-ttu-id="ffade-105">Belirli şifreleme algoritması çağırarak uygulayan bir nesne oluşturma **oluşturma** bu algoritma için Özet sınıf üzerinde yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ffade-105">Create an object that implements a particular cryptography algorithm by calling the **Create** method on the abstract class for that algorithm.</span></span>  
  
-   <span data-ttu-id="ffade-106">Belirli şifreleme algoritması çağırarak uygulayan bir nesne oluşturma <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ffade-106">Create an object that implements a particular cryptography algorithm by calling the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="ffade-107">Şifreleme algoritmalarını (örneğin, bir simetrik blok şifreleme) sınıfının çağırarak uygulayan bir nesne oluşturma **oluşturma** algoritma türü için Özet sınıf üzerinde yöntemi (gibi <xref:System.Security.Cryptography.SymmetricAlgorithm>).</span><span class="sxs-lookup"><span data-stu-id="ffade-107">Create an object that implements a class of cryptographic algorithms (such as a symmetric block cipher) by calling the **Create** method on the abstract class for that type of algorithm (such as <xref:System.Security.Cryptography.SymmetricAlgorithm>).</span></span>  
  
 <span data-ttu-id="ffade-108">Örneğin, bir geliştirici, bir dizi bayt SHA1 karmasını işlem istediğini varsayalım.</span><span class="sxs-lookup"><span data-stu-id="ffade-108">For example, suppose a developer wants to compute the SHA1 hash of a set of bytes.</span></span> <span data-ttu-id="ffade-109"><xref:System.Security.Cryptography> Ad alanı, SHA1 algoritması, tamamen yönetilen bir uygulama ve CryptoAPI saran bir, iki uygulamalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="ffade-109">The <xref:System.Security.Cryptography> namespace contains two implementations of the SHA1 algorithm, one purely managed implementation and one that wraps CryptoAPI.</span></span> <span data-ttu-id="ffade-110">Belirli bir SHA1 uygulama örneği oluşturmak geliştiricinin seçebilirsiniz (gibi <xref:System.Security.Cryptography.SHA1Managed>) çağırarak **yeni** işleci.</span><span class="sxs-lookup"><span data-stu-id="ffade-110">The developer can choose to instantiate a particular SHA1 implementation (such as the <xref:System.Security.Cryptography.SHA1Managed>) by calling the **new** operator.</span></span> <span data-ttu-id="ffade-111">Ortak dil çalışma zamanı yükler SHA1 karma algoritmasını sınıfı uygulayan sürece hangi sınıfın önemli değildir, ancak, geliştiricinin bir nesne çağırarak oluşturabilirsiniz <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ffade-111">However, if it does not matter which class the common language runtime loads as long as the class implements the SHA1 hash algorithm, the developer can create an object by calling the <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ffade-112">Bu yöntemi çağırır **System.Security.Cryptography.CryptoConfig.CreateFromName("System.Security.Cryptography.SHA1")**, SHA1 karma algoritmasını uygulaması döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="ffade-112">This method calls **System.Security.Cryptography.CryptoConfig.CreateFromName("System.Security.Cryptography.SHA1")**, which must return an implementation of the SHA1 hash algorithm.</span></span>  
  
 <span data-ttu-id="ffade-113">Geliştirici da çağırabilir **System.Security.Cryptography.CryptoConfig.CreateFromName("SHA1")** varsayılan olarak, .NET Framework'teki sevk algoritmalar için kısa adları şifreleme yapılandırması içerdiğinden.</span><span class="sxs-lookup"><span data-stu-id="ffade-113">The developer can also call **System.Security.Cryptography.CryptoConfig.CreateFromName("SHA1")** because, by default, cryptography configuration includes short names for the algorithms shipped in the .NET Framework.</span></span>  
  
 <span data-ttu-id="ffade-114">Karma algoritmayı kullanılan önemli değildir, geliştirici çağırabilirsiniz <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> yöntemi bir karma dönüştürmesi uygulayan bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="ffade-114">If it does not matter which hash algorithm is used, the developer can call the <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> method, which returns an object that implements a hashing transformation.</span></span>  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a><span data-ttu-id="ffade-115">Yapılandırma dosyalarında algoritma adlarını eşleme</span><span class="sxs-lookup"><span data-stu-id="ffade-115">Mapping Algorithm Names in Configuration Files</span></span>  
 <span data-ttu-id="ffade-116">Varsayılan olarak, çalışma zamanı döndüren bir <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> tüm dört senaryo için nesnesi.</span><span class="sxs-lookup"><span data-stu-id="ffade-116">By default, the runtime returns a <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> object for all four scenarios.</span></span> <span data-ttu-id="ffade-117">Ancak, bir Makine Yöneticisi son iki senaryo yöntemlerinde dönüş nesne türünü değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ffade-117">However, a machine administrator can change the type of object that the methods in the last two scenarios return.</span></span> <span data-ttu-id="ffade-118">Bunu yapmak için bir kolay algoritma adı makine yapılandırma dosyasındaki (Machine.config) kullanmak istediğiniz sınıfı eşlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="ffade-118">To do this, you must map a friendly algorithm name to the class you want to use in the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="ffade-119">Aşağıdaki örnek çalışma zamanı yapılandırmak nasıl gösterir şekilde **System.Security.Cryptography.SHA1.Create**, **System.Security.CryptoConfig.CreateFromName("SHA1")**, ve  **System.Security.Cryptography.HashAlgorithm.Create** dönüş bir `MySHA1HashClass` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="ffade-119">The following example shows how to configure the runtime so that **System.Security.Cryptography.SHA1.Create**, **System.Security.CryptoConfig.CreateFromName("SHA1")**, and **System.Security.Cryptography.HashAlgorithm.Create** return a `MySHA1HashClass` object.</span></span>  
  
```xml  
<configuration>  
   <!-- Other configuration settings. -->  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MySHA1Hash="MySHA1HashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="SHA1" class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.SHA1"  
                       class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MySHA1Hash"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 <span data-ttu-id="ffade-120">Özniteliğin adını belirtebilirsiniz [< cryptoClass\> öğesi](../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) (önceki örnekte öznitelik adları `MySHA1Hash`).</span><span class="sxs-lookup"><span data-stu-id="ffade-120">You can specify the name of the attribute in the [<cryptoClass\> element](../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) (the previous example names the attribute `MySHA1Hash`).</span></span> <span data-ttu-id="ffade-121">Özniteliğin değerini  **\<cryptoClass >** öğesidir ortak dil çalışma zamanı sınıfı bulmak için kullandığı bir dize.</span><span class="sxs-lookup"><span data-stu-id="ffade-121">The value of the attribute in the **\<cryptoClass>** element is a string that the common language runtime uses to find the class.</span></span> <span data-ttu-id="ffade-122">Belirtilen gereksinimleri karşılayan herhangi bir dize kullanabilirsiniz [belirtme tam olarak nitelenmiş tür adları](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="ffade-122">You can use any string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>  
  
 <span data-ttu-id="ffade-123">Çok sayıda algoritma adlarını aynı sınıfa eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ffade-123">Many algorithm names can map to the same class.</span></span> <span data-ttu-id="ffade-124">[ \<NameEntry > öğesi](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) bir sınıf için bir kolay algoritma adı eşler.</span><span class="sxs-lookup"><span data-stu-id="ffade-124">The [\<nameEntry> element](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) maps a class to one friendly algorithm name.</span></span> <span data-ttu-id="ffade-125">**Adı** özniteliği çağrılırken kullanılan ya da bir dize olabilir **System.Security.Cryptography.CryptoConfig.CreateFromName** soyutşifrelemesınıfındaadıveyayöntemi<xref:System.Security.Cryptography> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="ffade-125">The **name** attribute can be either a string that is used when calling the **System.Security.Cryptography.CryptoConfig.CreateFromName** method or the name of an abstract cryptography class in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="ffade-126">Değeri **sınıfı** özniteliği özniteliğinde adıdır  **\<cryptoClass >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="ffade-126">The value of the **class** attribute is the name of the attribute in the **\<cryptoClass>** element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ffade-127">SHA1 algoritması çağırarak alabileceğiniz <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> veya **Security.CryptoConfig.CreateFromName("SHA1")** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ffade-127">You can get an SHA1 algorithm by calling the <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> or the **Security.CryptoConfig.CreateFromName("SHA1")** method.</span></span> <span data-ttu-id="ffade-128">Her yöntem, yalnızca SHA1 algoritması uygulayan bir nesne döndürür güvence altına alır.</span><span class="sxs-lookup"><span data-stu-id="ffade-128">Each method guarantees only that it returns an object that implements the SHA1 algorithm.</span></span> <span data-ttu-id="ffade-129">Aynı sınıf yapılandırma dosyasındaki her bir algoritma kolay adını Eşle gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ffade-129">You do not have to map each friendly name of an algorithm to the same class in the configuration file.</span></span>  
  
 <span data-ttu-id="ffade-130">Varsayılan adlarını ve eşlemek için sınıflar listesi için bkz: <xref:System.Security.Cryptography.CryptoConfig>.</span><span class="sxs-lookup"><span data-stu-id="ffade-130">For a list of default names and the classes they map to, see <xref:System.Security.Cryptography.CryptoConfig>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffade-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ffade-131">See Also</span></span>  
 [<span data-ttu-id="ffade-132">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="ffade-132">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="ffade-133">Şifreleme sınıflarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ffade-133">Configuring Cryptography Classes</span></span>](../../../docs/framework/configure-apps/configure-cryptography-classes.md)
