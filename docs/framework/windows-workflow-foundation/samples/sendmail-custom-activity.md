---
title: SendMail Özel Etkinliği
ms.date: 03/30/2017
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
ms.openlocfilehash: 4dca15bfd3798b9282960663bea827f9323a1266
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547746"
---
# <a name="sendmail-custom-activity"></a><span data-ttu-id="0a14c-102">SendMail Özel Etkinliği</span><span class="sxs-lookup"><span data-stu-id="0a14c-102">SendMail Custom Activity</span></span>
<span data-ttu-id="0a14c-103">Bu örnek, <xref:System.Activities.AsyncCodeActivity> bir iş akışı uygulaması içinde kullanılmak üzere SMTP kullanarak posta göndermek için öğesinden türetilen özel bir etkinliğin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0a14c-103">This sample demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span> <span data-ttu-id="0a14c-104">Özel etkinlik, <xref:System.Net.Mail.SmtpClient> e-postayı zaman uyumsuz olarak göndermek ve kimlik doğrulamasıyla posta göndermek için yeteneklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0a14c-104">The custom activity uses the capabilities of <xref:System.Net.Mail.SmtpClient> to send email asynchronously and to send mail with authentication.</span></span> <span data-ttu-id="0a14c-105">Ayrıca, test modu, belirteç değiştirme, dosya şablonları ve test bırakma yolu gibi bazı son kullanıcı özellikleri de sağlar.</span><span class="sxs-lookup"><span data-stu-id="0a14c-105">It also provides some end-user features like test mode, token replacement, file templates, and test drop path.</span></span>  
  
 <span data-ttu-id="0a14c-106">Aşağıdaki tabloda etkinliğin bağımsız değişkenlerinin ayrıntıları verilmiştir `SendMail` .</span><span class="sxs-lookup"><span data-stu-id="0a14c-106">The following table details the arguments for the `SendMail` activity.</span></span>  
  
|<span data-ttu-id="0a14c-107">Ad</span><span class="sxs-lookup"><span data-stu-id="0a14c-107">Name</span></span>|<span data-ttu-id="0a14c-108">Tür</span><span class="sxs-lookup"><span data-stu-id="0a14c-108">Type</span></span>|<span data-ttu-id="0a14c-109">Description</span><span class="sxs-lookup"><span data-stu-id="0a14c-109">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="0a14c-110">Ana bilgisayar</span><span class="sxs-lookup"><span data-stu-id="0a14c-110">Host</span></span>|<span data-ttu-id="0a14c-111">Dize</span><span class="sxs-lookup"><span data-stu-id="0a14c-111">String</span></span>|<span data-ttu-id="0a14c-112">SMTP sunucusu konağının adresi.</span><span class="sxs-lookup"><span data-stu-id="0a14c-112">Address of the SMTP server host.</span></span>|  
|<span data-ttu-id="0a14c-113">Bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="0a14c-113">Port</span></span>|<span data-ttu-id="0a14c-114">Dize</span><span class="sxs-lookup"><span data-stu-id="0a14c-114">String</span></span>|<span data-ttu-id="0a14c-115">Konaktaki SMTP hizmetinin bağlantı noktası.</span><span class="sxs-lookup"><span data-stu-id="0a14c-115">Port of the SMTP service in the host.</span></span>|  
|<span data-ttu-id="0a14c-116">EnableSsl</span><span class="sxs-lookup"><span data-stu-id="0a14c-116">EnableSsl</span></span>|<span data-ttu-id="0a14c-117">bool</span><span class="sxs-lookup"><span data-stu-id="0a14c-117">bool</span></span>|<span data-ttu-id="0a14c-118"><xref:System.Net.Mail.SmtpClient>Bağlantının, bağlantıyı şifrelemek için Güvenli Yuva Katmanı (SSL) kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0a14c-118">Specifies whether the <xref:System.Net.Mail.SmtpClient> uses Secure Sockets Layer (SSL) to encrypt the connection.</span></span>|  
|<span data-ttu-id="0a14c-119">UserName</span><span class="sxs-lookup"><span data-stu-id="0a14c-119">UserName</span></span>|<span data-ttu-id="0a14c-120">Dize</span><span class="sxs-lookup"><span data-stu-id="0a14c-120">String</span></span>|<span data-ttu-id="0a14c-121">Gönderen özelliğinin kimlik doğrulaması için kimlik bilgilerini ayarlamak üzere Kullanıcı adı <xref:System.Net.Mail.SmtpClient.Credentials%2A> .</span><span class="sxs-lookup"><span data-stu-id="0a14c-121">Username to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="0a14c-122">Parola</span><span class="sxs-lookup"><span data-stu-id="0a14c-122">Password</span></span>|<span data-ttu-id="0a14c-123">Dize</span><span class="sxs-lookup"><span data-stu-id="0a14c-123">String</span></span>|<span data-ttu-id="0a14c-124">Gönderen özelliğinin kimlik doğrulaması için kimlik bilgilerini ayarlamak için parola <xref:System.Net.Mail.SmtpClient.Credentials%2A> .</span><span class="sxs-lookup"><span data-stu-id="0a14c-124">Password to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="0a14c-125">Konu</span><span class="sxs-lookup"><span data-stu-id="0a14c-125">Subject</span></span>|<xref:System.Activities.InArgument%601>\<string>|<span data-ttu-id="0a14c-126">İletinin konusu.</span><span class="sxs-lookup"><span data-stu-id="0a14c-126">Subject of the message.</span></span>|  
|<span data-ttu-id="0a14c-127">Gövde</span><span class="sxs-lookup"><span data-stu-id="0a14c-127">Body</span></span>|<xref:System.Activities.InArgument%601>\<string>|<span data-ttu-id="0a14c-128">İletinin gövdesi.</span><span class="sxs-lookup"><span data-stu-id="0a14c-128">Body of the message.</span></span>|  
|<span data-ttu-id="0a14c-129">Ekler</span><span class="sxs-lookup"><span data-stu-id="0a14c-129">Attachments</span></span>|<xref:System.Activities.InArgument%601>\<string>|<span data-ttu-id="0a14c-130">Bu e-posta iletisine eklenen verileri depolamak için kullanılan ek koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="0a14c-130">Attachment collection used to store data attached to this email message.</span></span>|  
|<span data-ttu-id="0a14c-131">Kaynak</span><span class="sxs-lookup"><span data-stu-id="0a14c-131">From</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="0a14c-132">Bu e-posta iletisinin Kimden adresi.</span><span class="sxs-lookup"><span data-stu-id="0a14c-132">From address for this email message.</span></span>|  
|<span data-ttu-id="0a14c-133">Amaç</span><span class="sxs-lookup"><span data-stu-id="0a14c-133">To</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="0a14c-134">Bu e-posta iletisinin alıcılarını içeren adres toplama.</span><span class="sxs-lookup"><span data-stu-id="0a14c-134">Address collection that contains the recipients of this email message.</span></span>|  
|<span data-ttu-id="0a14c-135">CC</span><span class="sxs-lookup"><span data-stu-id="0a14c-135">CC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="0a14c-136">Bu e-posta iletisi için karbon kopyası (CC) alıcılarını içeren adres toplama.</span><span class="sxs-lookup"><span data-stu-id="0a14c-136">Address collection that contains the carbon copy (CC) recipients for this email message.</span></span>|  
|<span data-ttu-id="0a14c-137">ALÝCÝ</span><span class="sxs-lookup"><span data-stu-id="0a14c-137">BCC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="0a14c-138">Bu e-posta iletisi için gizli bilgi kopyası (gızlı) alıcılarını içeren adres toplama.</span><span class="sxs-lookup"><span data-stu-id="0a14c-138">Address collection that contains the blind carbon copy (BCC) recipients for this email message.</span></span>|  
|<span data-ttu-id="0a14c-139">Belirteçler</span><span class="sxs-lookup"><span data-stu-id="0a14c-139">Tokens</span></span>|<span data-ttu-id="0a14c-140"><xref:System.Activities.InArgument%601><IDictionary\<string, string>></span><span class="sxs-lookup"><span data-stu-id="0a14c-140"><xref:System.Activities.InArgument%601><IDictionary\<string, string>></span></span>|<span data-ttu-id="0a14c-141">Gövdede değiştirilecek belirteçler.</span><span class="sxs-lookup"><span data-stu-id="0a14c-141">Tokens to replace in the body.</span></span> <span data-ttu-id="0a14c-142">Bu özellik, kullanıcıların gövdede daha sonra bu özellik kullanılarak girilen belirteçlerle değiştirilebilmesi için bazı değerler belirlemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="0a14c-142">This feature allows users to specify some values in the body than can be replaced later by the tokens provided using this property.</span></span>|  
|<span data-ttu-id="0a14c-143">BodyTemplateFilePath</span><span class="sxs-lookup"><span data-stu-id="0a14c-143">BodyTemplateFilePath</span></span>|<span data-ttu-id="0a14c-144">Dize</span><span class="sxs-lookup"><span data-stu-id="0a14c-144">String</span></span>|<span data-ttu-id="0a14c-145">Gövde şablonunun yolu.</span><span class="sxs-lookup"><span data-stu-id="0a14c-145">Path of a template for the body.</span></span> <span data-ttu-id="0a14c-146">`SendMail`Etkinlik bu dosyanın içeriğini Body özelliğine kopyalar.</span><span class="sxs-lookup"><span data-stu-id="0a14c-146">The `SendMail` activity copies the contents of this file to its body property.</span></span><br /><br /> <span data-ttu-id="0a14c-147">Şablon, belirteçler özelliğinin içeriğiyle değiştirilmiş belirteçleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="0a14c-147">The template can contain tokens that are replaced by the contents of the tokens property.</span></span>|  
|<span data-ttu-id="0a14c-148">TestMailTo</span><span class="sxs-lookup"><span data-stu-id="0a14c-148">TestMailTo</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="0a14c-149">Bu özellik ayarlandığında, tüm e-postalar içinde belirtilen adrese gönderilir.</span><span class="sxs-lookup"><span data-stu-id="0a14c-149">When this property is set, all emails are sent to the address specified in it.</span></span><br /><br /> <span data-ttu-id="0a14c-150">Bu özellik iş akışlarını test ederken kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0a14c-150">This property is intended to be used when testing workflows.</span></span> <span data-ttu-id="0a14c-151">Örneğin, tüm e-postaların gerçek alıcılara gönderilmeksizin gönderilmesini sağlamak istediğinizde.</span><span class="sxs-lookup"><span data-stu-id="0a14c-151">For example, when you want to make sure that all emails are sent without sending them to the actual recipients.</span></span>|  
|<span data-ttu-id="0a14c-152">TestDropPath</span><span class="sxs-lookup"><span data-stu-id="0a14c-152">TestDropPath</span></span>|<span data-ttu-id="0a14c-153">Dize</span><span class="sxs-lookup"><span data-stu-id="0a14c-153">String</span></span>|<span data-ttu-id="0a14c-154">Bu özellik ayarlandığında, tüm e-postalar da belirtilen dosyaya kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="0a14c-154">When this property is set, all emails are also saved in the specified file.</span></span><br /><br /> <span data-ttu-id="0a14c-155">Bu özellik, giden e-postaların biçiminin ve içeriğinin uygun olduğundan emin olmak için iş akışlarını test ederken veya hata ayıklarken kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0a14c-155">This property is intended to be used when you are testing or debugging workflows, to make sure that the format and contents of the outgoing emails is appropriate.</span></span>|  
  
## <a name="solution-contents"></a><span data-ttu-id="0a14c-156">Çözüm Içeriği</span><span class="sxs-lookup"><span data-stu-id="0a14c-156">Solution Contents</span></span>  
 <span data-ttu-id="0a14c-157">Çözüm iki proje içerir.</span><span class="sxs-lookup"><span data-stu-id="0a14c-157">The solution contains two projects.</span></span>  
  
|<span data-ttu-id="0a14c-158">Proje</span><span class="sxs-lookup"><span data-stu-id="0a14c-158">Project</span></span>|<span data-ttu-id="0a14c-159">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0a14c-159">Description</span></span>|<span data-ttu-id="0a14c-160">Önemli dosyalar</span><span class="sxs-lookup"><span data-stu-id="0a14c-160">Important Files</span></span>|  
|-------------|-----------------|---------------------|  
|<span data-ttu-id="0a14c-161">SendMail</span><span class="sxs-lookup"><span data-stu-id="0a14c-161">SendMail</span></span>|<span data-ttu-id="0a14c-162">SendMail etkinliği</span><span class="sxs-lookup"><span data-stu-id="0a14c-162">The SendMail activity</span></span>|<span data-ttu-id="0a14c-163">1. SendMail.cs: ana etkinlik için uygulama</span><span class="sxs-lookup"><span data-stu-id="0a14c-163">1.  SendMail.cs: implementation for the main activity</span></span><br /><span data-ttu-id="0a14c-164">SendMail etkinliği için 2. SendMailDesigner. xaml ve SendMailDesigner.xaml.cs: Designer</span><span class="sxs-lookup"><span data-stu-id="0a14c-164">2.  SendMailDesigner.xaml and SendMailDesigner.xaml.cs: designer for the SendMail activity</span></span><br /><span data-ttu-id="0a14c-165">3. MailTemplateBody.htm: gönderilecek e-postanın şablonu.</span><span class="sxs-lookup"><span data-stu-id="0a14c-165">3.  MailTemplateBody.htm: template for the email to be sent out.</span></span>|  
|<span data-ttu-id="0a14c-166">SendMailTestClient</span><span class="sxs-lookup"><span data-stu-id="0a14c-166">SendMailTestClient</span></span>|<span data-ttu-id="0a14c-167">SendMail etkinliğini test etmek için istemci.</span><span class="sxs-lookup"><span data-stu-id="0a14c-167">Client to test the SendMail activity.</span></span>  <span data-ttu-id="0a14c-168">Bu proje, SendMail etkinliğini çağırmanın iki yolunu gösterir: bildirimli ve programlı olarak.</span><span class="sxs-lookup"><span data-stu-id="0a14c-168">This project demonstrates two ways of invoking the SendMail activity: declaratively, and programmatically.</span></span>|<span data-ttu-id="0a14c-169">1. Sequence1. xaml: SendMail etkinliğini çağıran iş akışı.</span><span class="sxs-lookup"><span data-stu-id="0a14c-169">1.  Sequence1.xaml: workflow that invokes the SendMail activity.</span></span><br /><span data-ttu-id="0a14c-170">2. Program.cs: Sequence1 çağırır ve ayrıca SendMail kullanan programlı bir iş akışı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0a14c-170">2.  Program.cs: invokes Sequence1 and also creates a workflow programmatically that uses SendMail.</span></span>|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a><span data-ttu-id="0a14c-171">SendMail etkinliğinin daha fazla yapılandırması</span><span class="sxs-lookup"><span data-stu-id="0a14c-171">Further configuration of the SendMail activity</span></span>  
 <span data-ttu-id="0a14c-172">Örnekte gösterilmese de, kullanıcılar SendMail etkinliğinin ek yapılandırmasını gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="0a14c-172">Although not shown in the sample, users can perform addition configuration of the SendMail activity.</span></span> <span data-ttu-id="0a14c-173">Sonraki üç bölümde bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0a14c-173">The next three sections demonstrate how this is done.</span></span>  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a><span data-ttu-id="0a14c-174">Gövdede belirtilen belirteçleri kullanarak e-posta gönderme</span><span class="sxs-lookup"><span data-stu-id="0a14c-174">Sending an email using tokens specified in the body</span></span>  
 <span data-ttu-id="0a14c-175">Bu kod parçacığı, gövdedeki belirteçlerle nasıl e-posta gönderebileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="0a14c-175">This code snippet demonstrates how you can send email with tokens in the body.</span></span> <span data-ttu-id="0a14c-176">Gövde özelliğinde belirteçlerin nasıl sağlandığını fark edin.</span><span class="sxs-lookup"><span data-stu-id="0a14c-176">Notice how the tokens are provided in the body property.</span></span> <span data-ttu-id="0a14c-177">Bu belirteçlerin değerleri belirteçler özelliğine sağlanır.</span><span class="sxs-lookup"><span data-stu-id="0a14c-177">Values for those tokens are provided to the tokens property.</span></span>  
  
```csharp  
IDictionary<string, string> tokens = new Dictionary<string, string>();  
tokens.Add("@name", "John Doe");  
tokens.Add("@date", DateTime.Now.ToString());  
tokens.Add("@server", "localhost");  
  
new SendMail  
{  
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Body = "Hello @name. This is a test email sent from @server. Current date is @date",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens)  
};  
```  
  
### <a name="sending-an-email-using-a-template"></a><span data-ttu-id="0a14c-178">Şablon kullanarak e-posta gönderme</span><span class="sxs-lookup"><span data-stu-id="0a14c-178">Sending an email using a template</span></span>  
 <span data-ttu-id="0a14c-179">Bu kod parçacığında, gövdedeki bir şablon belirteçlerini kullanarak e-posta gönderme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0a14c-179">This snippet shows how to send an email using a template tokens in the body.</span></span> <span data-ttu-id="0a14c-180">`BodyTemplateFilePath`Gövde özelliği için değer sağlamak zorunda olduğumuz özelliği ayarlarken (şablon dosyasının içeriği gövdeye kopyalanacaktır) dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="0a14c-180">Notice that when setting the `BodyTemplateFilePath` property we don’t need to provide the value for Body property (the contents of the template file will be copied to the body).</span></span>  
  
```csharp  
new SendMail  
{
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
    BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",
};  
```  
  
### <a name="sending-mails-in-testing-mode"></a><span data-ttu-id="0a14c-181">Sınama modunda postaları gönderme</span><span class="sxs-lookup"><span data-stu-id="0a14c-181">Sending Mails in Testing Mode</span></span>  
 <span data-ttu-id="0a14c-182">Bu kod parçacığı, iki test özelliklerinin nasıl ayarlanacağını gösterir: ayarına göre `TestMailTo` , tüm iletiler için gönderilir `john.doe@contoso.con` (Kime, CC, gizli değerleri olmadan).</span><span class="sxs-lookup"><span data-stu-id="0a14c-182">This code snippet shows how to set the two testing properties: by setting `TestMailTo` to all messages will be sent to `john.doe@contoso.con` (without regard of the values of To, Cc, Bcc).</span></span> <span data-ttu-id="0a14c-183">TestDropPath ' i ayarlayarak tüm giden e-postalar da, belirtilen yola kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="0a14c-183">By setting TestDropPath all outgoing emails will be also recorded in the provided path.</span></span> <span data-ttu-id="0a14c-184">Bu özellikler bağımsız olarak ayarlanabilir (ilişkili değildir).</span><span class="sxs-lookup"><span data-stu-id="0a14c-184">These properties can be set independently (they are not related).</span></span>  
  
```csharp  
new SendMail  
{
   From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
   Subject = "Test email",  
   Host = "localhost",  
   Port = 25,  
   Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
   BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",  
   TestMailTo= new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   TestDropPath = @"c:\Samples\SendMail\TestDropPath\",  
};  
```  
  
## <a name="set-up-instructions"></a><span data-ttu-id="0a14c-185">Kurulum Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="0a14c-185">Set-Up Instructions</span></span>  
 <span data-ttu-id="0a14c-186">Bu örnek için bir SMTP sunucusuna erişim gerekir.</span><span class="sxs-lookup"><span data-stu-id="0a14c-186">Access to a SMTP server is required for this sample.</span></span>  
  
 <span data-ttu-id="0a14c-187">SMTP sunucusu kurma hakkında daha fazla bilgi için aşağıdaki bağlantılara bakın.</span><span class="sxs-lookup"><span data-stu-id="0a14c-187">For more information about setting up a SMTP server, see the following links.</span></span>  
  
- <span data-ttu-id="0a14c-188">[SMTP hizmetini yapılandırma (IIS 6,0)](/previous-versions/windows/it-pro/windows-server-2003/cc784968(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="0a14c-188">[Configuring the SMTP Service (IIS 6.0)](/previous-versions/windows/it-pro/windows-server-2003/cc784968(v=ws.10))</span></span>  
  
- <span data-ttu-id="0a14c-189">[IIS 7,0: SMTP e-postasını Yapılandırma](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772058(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="0a14c-189">[IIS 7.0: Configure SMTP E-Mail](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772058(v=ws.10))</span></span>  
  
- <span data-ttu-id="0a14c-190">[SMTP hizmetini nasıl yükleyeceğiniz](/previous-versions/tn-archive/aa997480(v=exchg.65))</span><span class="sxs-lookup"><span data-stu-id="0a14c-190">[How to Install the SMTP Service](/previous-versions/tn-archive/aa997480(v=exchg.65))</span></span>  
  
 <span data-ttu-id="0a14c-191">Üçüncü taraflar tarafından sağlanan SMTP öykünücüleri indirilebilir.</span><span class="sxs-lookup"><span data-stu-id="0a14c-191">SMTP emulators provided by third parties are available for download.</span></span>  
  
##### <a name="to-run-this-sample"></a><span data-ttu-id="0a14c-192">Bu örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="0a14c-192">To run this sample</span></span>  
  
1. <span data-ttu-id="0a14c-193">Visual Studio 2010 kullanarak SendMail. sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="0a14c-193">Using Visual Studio 2010, open the SendMail.sln solution file.</span></span>  
  
2. <span data-ttu-id="0a14c-194">Geçerli bir SMTP sunucusuna erişiminiz olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="0a14c-194">Ensure that you have access to a valid SMTP server.</span></span> <span data-ttu-id="0a14c-195">Bkz. kurulum yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="0a14c-195">See the set-up instructions.</span></span>  
  
3. <span data-ttu-id="0a14c-196">Programı sunucu adresinizle ve Kimden e-posta adreslerinden yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="0a14c-196">Configure the program with your server address, and From and To email addresses.</span></span>  
  
     <span data-ttu-id="0a14c-197">Bu örneği doğru bir şekilde çalıştırmak için, ' ın ve e-posta adresleri ve Program.cs içindeki SMTP sunucusunun adresi ve dizi. xaml içindeki adresini yapılandırmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="0a14c-197">To correctly run this sample, you may need to configure the value of From and To email addresses and the address of the SMTP server in  Program.cs and in Sequence.xaml.</span></span> <span data-ttu-id="0a14c-198">Program postayı iki farklı şekilde gönderdiğinden, her iki konumdaki adresi de değiştirmeniz gerekir</span><span class="sxs-lookup"><span data-stu-id="0a14c-198">You will need to change the address in both locations since the program sends mail in two different ways</span></span>  
  
4. <span data-ttu-id="0a14c-199">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="0a14c-199">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5. <span data-ttu-id="0a14c-200">Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="0a14c-200">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0a14c-201">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="0a14c-201">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0a14c-202">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="0a14c-202">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="0a14c-203">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0a14c-203">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0a14c-204">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="0a14c-204">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`
